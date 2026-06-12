---
title: "Issues with my hard drive mounting during boot"
date: 2010-11-04
forum: General Help
---

### Post by vdubhack on 2010-11-04
Running 10.10 64bit Kernel 2.6.35-23

I am noticing what I think is a big hiccup in my boot process my drive is mounting at around the 4sec mark then my system pauses for roughly 13 seconds, you can even it see it on the screen a blinking cursor comes up the entire time. Then during the rest of the boot my drive will re-mount at least 4 more times. Then during use of my system there will be random re-mounts throughout the use. 

Here is the mounting message
```
 4.935976] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   17.006924] Adding 5125116k swap on /dev/sda4.  Priority:-1 extents:1 across:5125116k 
```These are the repeated re-mounting messages during boot. generally my last or second to last message in dmesg ends with this every boot. This is the first re-mount message 
```
EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
```The rest of the re-mount messages are like this
```
EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
```I just noticed the pausing recently after an update but have been seeing this re-mounting since install. Are these normal? They dont seem like it to me, and if they are normal why such a long time on the initial mount and every re-mount takes 4-5 seconds. Let me know if I can provide any further info as well. Thanks for any info and or help on this.

---

### Post by vdubhack on 2010-11-06
Anyone have any ideas and or suggestions on this ?

---

### Post by sohlinux on 2010-11-06
sounds like you may have a bad drive. try to boot with the live cd and check the drive

---

### Post by vdubhack on 2010-11-06
I have run multiple dish checks and never reports a problem I have tried in both linux and windows and neither ever report issues at all about my disk. 

I just get those messages a ton and when shutting down I get a message that says unmounting weak file systems. 

I have run fsck the logs say nothings logged. gsmartcontrol says disks are fine as well. 

So dont think its a bad drive, but if you have other suggestions on how to find whats wrong with it I am open to try and figure it out.


edit: 

Could it be the SATA  is not being setup properly or something: 

```
[    2.460743] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x39 impl SATA mode
[    2.521937] ata1: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908100 irq 50
[    2.521947] ata4: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908280 irq 50
[    2.521953] ata5: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908300 irq 50
[    2.521960] ata6: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908380 irq 50
[    2.870504] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.237245] ata4: SATA link down (SStatus 0 SControl 300)
[    4.017463] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.397323] ata6: SATA link down (SStatus 0 SControl 300)

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host0 to max_performance...Done.
Setting SATA APLM on host1 to max_performance...Done.
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.
Setting SATA APLM on host4 to max_performance...Done.
Setting SATA APLM on host5 to max_performance...Done.

```Just saw these messages not sure it helps any There is only one HD in my laptop

---

### Post by sohlinux on 2010-11-06
as its a laptop it could be some power issue, check in the power options - system power management and set to never sleep and not to spin down hard drives

and try cleaning the file system

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1578000](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1578000)

---

### Post by vdubhack on 2010-11-06
I had already found that thread and tried everything on there and still have the issue. This is on a clean install and I have tried installing 3 different times. So I just do not get whats up with this.

---

### Post by vdubhack on 2010-11-06
I just found these messages in dmesg seems the SATA link goes down and then it re-mounts

```
[    0.000000]  BIOS-e820: 00000000bf7cc000 - 00000000bf7ff000 (ACPI data)
[    0.000000]  modified: 00000000bf7cc000 - 00000000bf7ff000 (ACPI data)
[    0.000000] Memory: 3902340k/5242880k available (5710k kernel code, 1060432k absent, 280108k reserved, 5380k data, 908k init)
[    1.762374] ACPI: EC: GPE = 0x1e, I/O: command/status = 0x66, data = 0x62
[    1.763690] _OSC request data:1 8 1f 
[    1.829635] _OSC request data:1 1f 1f 
[    1.845801] libata version 3.00 loaded.
[    1.946933] _OSC request data:1 0 1f 
[    1.947096] _OSC request data:1 0 1f 
[    1.947246] _OSC request data:1 0 1f 
[    1.947394] _OSC request data:1 0 1f 
[    1.947540] _OSC request data:1 0 1f 
[    1.947701] _OSC request data:1 0 1f 
[    1.947849] _OSC request data:1 0 1f 
[    1.947996] _OSC request data:1 0 1f 
[    1.948142] _OSC request data:1 0 1f 
[    2.342793] Write protecting the kernel read-only data: 10240k
[    2.501609] ata1: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908100 irq 50
[    2.501611] ata2: DUMMY
[    2.501612] ata3: DUMMY
[    2.501619] ata4: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908280 irq 50
[    2.501625] ata5: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908300 irq 50
[    2.501665] ata6: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908380 irq 50
[    2.850323] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.851515] ata1.00: ATA-8: Hitachi HTS725050A9A360, PC4OC71E, max UDMA/133
[    2.851523] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.852988] ata1.00: configured for UDMA/133
[    3.217108] ata4: SATA link down (SStatus 0 SControl 300)
[    3.989762] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.991212] ata5.00: ATAPI: MATSHITABD-CMB UJ141EL, 1.00, max UDMA/100
[    3.993320] ata5.00: configured for UDMA/100
[    4.356611] ata6: SATA link down (SStatus 0 SControl 300)
[    4.809529] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
``````
[    4.809529] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   16.523997] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   18.564832] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   28.669951] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
``````
[    2.439914] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x39 impl SATA mode
[    2.501609] ata1: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908100 irq 50
[    2.501619] ata4: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908280 irq 50
[    2.501625] ata5: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908300 irq 50
[    2.501665] ata6: SATA max UDMA/133 abar m2048@0xf0908000 port 0xf0908380 irq 50
[    2.850323] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.217108] ata4: SATA link down (SStatus 0 SControl 300)
[    3.989762] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.356611] ata6: SATA link down (SStatus 0 SControl 300)
``````
[   16.523997] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   18.564832] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   28.669951] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
```Not sure what else to even look for or search online for now at this point. There is a second hard drive slot on the laptop that is not being used at this time could it be thinking its there or trying to mount that first and causing issues or ? Just throwing out ideas.

---

### Post by sohlinux on 2010-11-06
did you try to reset your bios settings to default?

---

### Post by sohlinux on 2010-11-06
can you paste in your /etc/fstab here

---

### Post by vdubhack on 2010-11-06
I never did anything to my bios its as it came from the factory. 

Here is fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=8b1aeb39-7a1a-423e-8b75-c576c0ec3a76 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=bf9c52d9-458e-4402-bd32-8735fad9e5e1 none            swap    sw              0       0
```Here is dmesg info on the UUID's in case this helps as well
```

[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=8b1aeb39-7a1a-423e-8b75-c576c0ec3a76 ro crashkernel=384M-2G:64M,2G-:128M nouveau.blacklist=1 quiet splash acpi_osi=Linux
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=8b1aeb39-7a1a-423e-8b75-c576c0ec3a76 ro crashkernel=384M-2G:64M,2G-:128M nouveau.blacklist=1 quiet splash acpi_osi=Linux
[    1.763688] \_SB_.PCI0:_OSC invalid UUID
[    1.829633] \_SB_.PCI0:_OSC invalid UUID
[    1.946931] \_SB_.PCI0:_OSC invalid UUID
[    1.947094] \_SB_.PCI0:_OSC invalid UUID
[    1.947245] \_SB_.PCI0:_OSC invalid UUID
[    1.947392] \_SB_.PCI0:_OSC invalid UUID
[    1.947538] \_SB_.PCI0:_OSC invalid UUID
[    1.947700] \_SB_.PCI0:_OSC invalid UUID
[    1.947847] \_SB_.PCI0:_OSC invalid UUID
[    1.947994] \_SB_.PCI0:_OSC invalid UUID
[    1.948140] \_SB_.PCI0:_OSC invalid UUID

```Thanks for your help so far with this very appreciated


From looking at the fstab's info online I am noticing mine does not have relatime option in it and my cd/dvd drive is not on there or is that all unrelated to this?

---

### Post by sohlinux on 2010-11-06
its a difficult one, you have an invalid UUID but maybe some synchronising problems or bad file system, you could install mountmanager from ubuntu software center and try the various options but backup your all files before hand just in case

---

### Post by vdubhack on 2010-11-07
I dont think those are even related to the hard drive though here is the full message 
```
[    2.316614] pcieport 0000:00:1c.6: setting latency timer to 64
[    2.316650]   alloc irq_desc for 49 on node -1
[    2.316651]   alloc kstat_irqs on node -1
[    2.316663] pcieport 0000:00:1c.6: irq 49 for MSI/MSI-X
[    2.316895] \_SB_.PCI0:_OSC invalid UUID
[    2.316897] _OSC request data:1 0 1f 
[    2.316901] aer 0000:00:03.0:pcie02: AER service couldn't init device: _OSC failed
[    2.316924] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.317058] \_SB_.PCI0:_OSC invalid UUID
[    2.317060] _OSC request data:1 0 1f 
[    2.317208] \_SB_.PCI0:_OSC invalid UUID
[    2.317210] _OSC request data:1 0 1f 
[    2.317355] \_SB_.PCI0:_OSC invalid UUID
[    2.317357] _OSC request data:1 0 1f 
[    2.317502] \_SB_.PCI0:_OSC invalid UUID
[    2.317503] _OSC request data:1 0 1f 
[    2.317663] \_SB_.PCI0:_OSC invalid UUID
[    2.317665] _OSC request data:1 0 1f 
[    2.317811] \_SB_.PCI0:_OSC invalid UUID
[    2.317813] _OSC request data:1 0 1f 
[    2.317957] \_SB_.PCI0:_OSC invalid UUID
[    2.317958] _OSC request data:1 0 1f 
[    2.318103] \_SB_.PCI0:_OSC invalid UUID
[    2.318105] _OSC request data:1 0 1f 
[    2.318133] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

```Here is another
```
[    2.187513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.187878] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    2.188113] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    2.188453] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    2.188678] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    2.188892] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    2.189106] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP07._PRT]
[    2.189412] \_SB_.PCI0:_OSC invalid UUID
[    2.189414] _OSC request data:1 1f 1f 
[    2.202818] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])

```This I have filed a bug report on but have yet to get any feedback or info about it and filed it I think almost 2 weeks ago now. 
```
[    2.122131] ACPI: EC: GPE = 0x1e, I/O: command/status = 0x66, data = 0x62
[    2.122451] ACPI: No dock devices found.
[    2.122454] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    2.123447] \_SB_.PCI0:_OSC invalid UUID
[    2.123449] _OSC request data:1 8 1f 
[    2.123454] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    2.124870] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    2.124874] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    2.124877] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    2.124880] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    2.124882] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    2.124885] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    2.124888] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    2.124993] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    2.124996] pci 0000:00:03.0: PME# disabled
[    2.125317] pci 0000:00:1a.0: reg 10: [mem 0xf0906000-0xf09063ff]
[    2.125382] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    2.125391] pci 0000:00:1a.0: PME# disabled
[    2.125443] pci 0000:00:1b.0: reg 10: [mem 0xf0900000-0xf0903fff 64bit]
[    2.125495] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    2.125503] pci 0000:00:1b.0: PME# disabled
[    2.125583] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    2.125592] pci 0000:00:1c.0: PME# disabled
[    2.125675] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    2.125684] pci 0000:00:1c.3: PME# disabled
[    2.125765] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    2.125773] pci 0000:00:1c.4: PME# disabled
[    2.125855] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    2.125864] pci 0000:00:1c.6: PME# disabled
[    2.125920] pci 0000:00:1d.0: reg 10: [mem 0xf0907000-0xf09073ff]
[    2.125985] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    2.125994] pci 0000:00:1d.0: PME# disabled
[    2.126208] pci 0000:00:1f.2: reg 10: [io  0x1830-0x1837]
[    2.126219] pci 0000:00:1f.2: reg 14: [io  0x1824-0x1827]
[    2.126229] pci 0000:00:1f.2: reg 18: [io  0x1828-0x182f]
[    2.126240] pci 0000:00:1f.2: reg 1c: [io  0x1820-0x1823]
[    2.126250] pci 0000:00:1f.2: reg 20: [io  0x1800-0x181f]
[    2.126261] pci 0000:00:1f.2: reg 24: [mem 0xf0908000-0xf09087ff]
[    2.126302] pci 0000:00:1f.2: PME# supported from D3hot
[    2.126311] pci 0000:00:1f.2: PME# disabled
[    2.126352] pci 0000:00:1f.3: reg 10: [mem 0xf0909000-0xf09090ff 64bit]
[    2.126370] pci 0000:00:1f.3: reg 20: [io  0x1840-0x185f]
[    2.126449] pci 0000:01:00.0: reg 10: [mem 0xcc000000-0xccffffff]
[    2.126457] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    2.126467] pci 0000:01:00.0: reg 1c: [mem 0xce000000-0xcfffffff 64bit pref]
[    2.126474] pci 0000:01:00.0: reg 24: [io  0x2000-0x207f]
[    2.126481] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    2.126533] pci 0000:01:00.1: reg 10: [mem 0xcdefc000-0xcdefffff]
[    2.126606] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    2.126610] pci 0000:00:03.0:   bridge window [io  0x2000-0x2fff]
[    2.126614] pci 0000:00:03.0:   bridge window [mem 0xcc000000-0xcdefffff]
[    2.126619] pci 0000:00:03.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    2.126670] pci 0000:00:1c.0: PCI bridge to [bus 02-04]
[    2.126679] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    2.126688] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf03fffff]
[    2.126699] pci 0000:00:1c.0:   bridge window [mem 0xf0a00000-0xf0bfffff 64bit pref]
[    2.126786] pci 0000:07:00.0: reg 10: [mem 0x00000000-0x00000fff]
[    2.126867] pci 0000:07:00.0: supports D1 D2
[    2.126869] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    2.126878] pci 0000:07:00.0: PME# disabled
[    2.126939] pci 0000:07:00.1: reg 10: [mem 0xf0501000-0xf05010ff]
[    2.127019] pci 0000:07:00.1: supports D1 D2
[    2.127021] pci 0000:07:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    2.127031] pci 0000:07:00.1: PME# disabled
[    2.127088] pci 0000:07:00.2: reg 10: [mem 0xf0503000-0xf0503fff]
[    2.127107] pci 0000:07:00.2: reg 18: [mem 0xf0502000-0xf05027ff]
[    2.127175] pci 0000:07:00.2: supports D1 D2
[    2.127177] pci 0000:07:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    2.127186] pci 0000:07:00.2: PME# disabled
[    2.147337] pci 0000:00:1c.3: PCI bridge to [bus 07-07]
[    2.147346] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    2.147355] pci 0000:00:1c.3:   bridge window [mem 0xf0500000-0xf05fffff]
[    2.147366] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.147465] pci 0000:0a:00.0: reg 10: [io  0x4000-0x40ff]
[    2.147477] pci 0000:0a:00.0: reg 14: [mem 0xf0600000-0xf0603fff]
[    2.147555] pci 0000:0a:00.0: supports D1 D2
[    2.147557] pci 0000:0a:00.0: PME# supported from D0 D1 D2 D3hot
[    2.147566] pci 0000:0a:00.0: PME# disabled
[    2.167319] pci 0000:00:1c.4: PCI bridge to [bus 0a-0a]
[    2.167329] pci 0000:00:1c.4:   bridge window [io  0x4000-0x4fff]
[    2.167338] pci 0000:00:1c.4:   bridge window [mem 0xf0600000-0xf06fffff]
[    2.167349] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.167446] pci 0000:0b:00.0: reg 10: [mem 0xf0400000-0xf043ffff 64bit]
[    2.167458] pci 0000:0b:00.0: reg 18: [io  0x5000-0x507f]
[    2.167531] pci 0000:0b:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    2.167541] pci 0000:0b:00.0: PME# disabled
[    2.187308] pci 0000:00:1c.6: PCI bridge to [bus 0b-0b]
[    2.187317] pci 0000:00:1c.6:   bridge window [io  0x5000-0x5fff]
[    2.187326] pci 0000:00:1c.6:   bridge window [mem 0xf0400000-0xf04fffff]
[    2.187337] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.187415] pci 0000:00:1e.0: PCI bridge to [bus 0c-0c] (subtractive decode)
[    2.187424] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    2.187433] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    2.187444] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.187447] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    2.187450] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    2.187452] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    2.187455] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    2.187458] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    2.187461] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    2.187463] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    2.187513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.187878] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    2.188113] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    2.188453] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    2.188678] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    2.188892] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    2.189106] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP07._PRT]
[    2.189412] \_SB_.PCI0:_OSC invalid UUID
[    2.189414] _OSC request data:1 1f 1f 
[    2.202818] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    2.203818] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    2.204009] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    2.204196] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    2.204383] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    2.204567] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    2.204755] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    2.204942] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    2.205129] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    2.205222] HEST: Table is not found!
[    2.205301] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    2.205312] vgaarb: loaded
[    2.205439] SCSI subsystem initialized

```
Not really sure what mount manager would accomplish? I have seen more than myself with weird re-mounting issues since 10.04 on all varying types of laptops some remount with 600 some 300 some 0 some all.


edit: the weak file system message seems to be gone, but stuff on shutdown always seems to go so fast I may be missing it right now. I have never seen it in any logs or anything.

---

### Post by dcstar on 2010-11-07
> **vdubhack said:**
> Running 10.10 64bit Kernel 2.6.35-23

I am noticing what I think is a big hiccup in my boot process my drive is mounting at around the 4sec mark then my system pauses for roughly 13 seconds,
........

Go to the Hardware and Laptops forum and see if others have similar issues.

---

### Post by vdubhack on 2010-11-07
> **dcstar said:**
> Go to the Hardware and Laptops forum and see if others have similar issues.


I have been searching this for a long while now and continue to even though I posted here. I am not finding anything that relates directly to the issues I am seeing as this is not all of the issues in itself. This happens on the .35-22 kernel as well so I dont think its a kernel related thing. I have already tried booting a previous version.

If you have seen something specific relating to what I have posted here please do show me the light, but as of now the only thing I can do with whats been mentioned to whats online is get the boot pause to increase nothing improves it. 

Though I think from my readings the weak file system on system shutdown is relating to a USB drive I have in sometimes thats formatted NTFS, and I read that, that message shows up when other file systems are mounted on shutdown. I removed the drive on next shutdown and no more message I have yet to put it back in and try that for sure, but looking that way at this point.

---

### Post by vdubhack on 2010-11-07
Just made a new partition and did yet another fresh install and from the get go on .35-22 kernel I get unmounting weak file system though no long pause in boot anymore. Also booting from the live cd gives the same results of remounting the drive multiple times. I noticed in grub it has ro in the boot args, tried booting without it and did not notice any difference. 

So I am lost as to whats going on and whats causing the improper UUID messages though I think its to other devices in the laptop as only 1 of 2 fans seem to run and there is an external sata/usb combo port that doesnt seem to work properly and a few other things. Also on this kernel the SD card reader does not get recognized until doing a work around. 

Maybe ACPI is not properly setting up all the devices. Never thought I would say I regret buying a new laptop


I think maybe power management is messing with this from this in dmesg 
```
[    2.006102] lo: Disabled Privacy Extensions
[    2.006304] NET: Registered protocol family 17
[    2.012282] PM: Resume from disk failed.
[    2.012288] registered taskstats version 1
[    2.012653]   Magic number: 2:725:4
[    2.012777] rtc_cmos 00:05: setting system clock to 2010-11-07 02:02:55 UTC (1289095375)

```

---

### Post by 73ckn797 on 2010-11-07
It may be a long shot but make sure the hard drive is connected securely and/or there is no dust in the connector. 

I have one desktop computer that was acting up and making me think the drive was failing due to a bad connection. the drive would work fine on multiple reboots then would not. Typically would happen if the box was moved any. I realize that the connections are different between a laptop and desktop but your issue could be just that simple.

---

### Post by sohlinux on 2010-11-07
I would try mountmanager with a few different settings

try remount on and off , and suid on and off

did you recently have windows running ok on this laptop?

options

atime,suid,mand,remount,group,dirsync,encryption,keybits,nouser,auto,rw,dev,exec,sync,allow_other,large_read,umask=777,fmask=777,dmask=666,ro,default,force,show_sys_files,silent,debug

---

### Post by sohlinux on 2010-11-07
what make and model is the laptop? there may be a bios update for it.

---

### Post by jBilbo on 2010-11-11
This happens because of this script:

```
/usr/lib/pm-utils/power.d/journal-commit
```

This script is from pm-utils package (power management) and is hooked to all power events (like plug/unplug the power cable).

Every time this script gets executed, it's changing the "commit" value of your ext4 partition. Commit value of 0 is the default and minimum (5 seconds, commit=0 equals commit=5), but growing this number improve performance (600 = 10minutes until journal data commits).

So this is not an error. However, you can disable this remount-to-change-commit-value behaviour doing:

```
sudo chmod -x /usr/lib/pm-utils/power.d/journal-commit
```

---

### Post by www.rzr.online.fr on 2011-11-01
I dont think this message :

  "\_SB_.PCI0:_OSC invalid UUID"

... is related to filestem , this looks like a broken ACPI table.


I am investigating on lenovo g470 :

[http://rzr.online.fr/q/dmesg](http://rzr.online.fr/q/dmesg)


Please confirm what BIOS version are you using ?

---

### Post by vdubhack on 2011-11-02
Here is the info you wanted.
```

*-core
       description: Motherboard
       product: Qosmio X505
       vendor: TOSHIBA
       physical id: 0
       version: Not Applicable
     
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V2.90
          date: 12/10/2010
          size: 112KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb biosbootspecification

```Our dmesg outputs look very similar this has been going on with me for a long time and MANY Kernel versions, tried posting bug reports and since there was very little response to it nothing ever came of it. If you would like any other info since you are trying to fix this let me know, I can boot from what ever Ubuntu version you would like and get info from it. I also see this on Fedora again .. What are you looking at as far as fixes? Would love to know what to even look at or how to try different things to see if they help. This is also suppose to be the most current BIOS version for my laptop which is a Toshiba qosmio x505-Q887.

Here is a link to my most current BIOS the last update in December was an ACPI update [http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=2681251&rpn=PQX33U&modelFilter=X505-Q887&selCategory=2756709&selFamily=804517](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=2681251&rpn=PQX33U&modelFilter=X505-Q887&selCategory=2756709&selFamily=804517)

---

