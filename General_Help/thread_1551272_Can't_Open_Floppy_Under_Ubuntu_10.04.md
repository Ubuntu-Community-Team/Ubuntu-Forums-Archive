---
title: "Can't Open Floppy Under Ubuntu 10.04"
date: 2010-08-12
forum: General Help
---

### Post by ilgaar on 2010-08-12
I tried to access my USB Floppy yesterday, I plugged it in, I could see it under Places/Computer, but I can not open the floppy, it just doesn't open, it's there, I right click to see what are my options, whether or not I can mount it but surprisingly there was no mount option in the menu, I tried to mount it manually from terminal, but nothing happens, which is very odd. I never had this problem using my Floppy drive back with other versions of Ubuntu. Could you please help me, what should I do? What could be causing this problem? How can I solve it to enjoy again using my Floppy drive?

Thank you for your understanding and support.

---

### Post by JustinR on 2010-08-12
> **ilgaar said:**
> I tried to access my USB Floppy yesterday, I plugged it in, I could see it under Places/Computer, but I can not open the floppy, it just doesn't open, it's there, I right click to see what are my options, whether or not I can mount it but surprisingly there was no mount option in the menu, I tried to mount it manually from terminal, but nothing happens, which is very odd. I never had this problem using my Floppy drive back with other versions of Ubuntu. Could you please help me, what should I do? What could be causing this problem? How can I solve it to enjoy again using my Floppy drive?

Thank you for your understanding and support.

Hi, can you post the output of this terminal command:

```

dmesg | tail -40

```

---

### Post by ilgaar on 2010-08-12
Hello, thanks for the reply. here is the output:

ilgaar@ilgaar-laptop:~$ dmesg | tail -40
[   47.154893] Bluetooth: RFCOMM ver 1.11
[   48.340161] eth0: no IPv6 routers present
[  215.533368] __ratelimit: 15 callbacks suppressed
[  215.533380] operapluginwrap[2693]: segfault at 0 ip (null) sp bfe1992c error 4 in libX11.so.6.3.0[110000+119000]
[  215.584588] operapluginwrap[2696]: segfault at 0 ip (null) sp bf9a04dc error 4 in libdl-2.11.1.so[110000+2000]
[  215.640462] operapluginwrap[2698]: segfault at 0 ip (null) sp bfce0c4c error 4 in libX11.so.6.3.0[110000+119000]
[  215.658473] operapluginwrap[2699]: segfault at 0 ip (null) sp bfc94b5c error 4 in libm-2.11.1.so[110000+24000]
[  215.669552] operapluginwrap[2700]: segfault at 0 ip (null) sp bffc951c error 4 in libXt.so.6.0.0[110000+4f000]
[  215.677935] operapluginwrap[2701]: segfault at 0 ip (null) sp bfe096cc error 4 in libXext.so.6.4.0[110000+e000]
[  215.688881] operapluginwrap[2703]: segfault at 0 ip (null) sp bfb9879c error 4 in libstdc++.so.6.0.13[110000+e9000]
[  215.695694] operapluginwrap[2704]: segfault at 0 ip (null) sp bfdfd1ec error 4 in libstdc++.so.6.0.13[110000+e9000]
[  619.706897] PPP MPPE Compression module registered
[ 1533.880807] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 1533.880812] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[ 1533.880814] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[ 1533.880816] vboxdrv: the usage of hardware performance counters by
[ 1533.880817] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[ 1533.880821] vboxdrv: Found 1 processor cores.
[ 1533.882533] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[ 1533.882537] vboxdrv: Successfully loaded version 3.2.8 (interface 0x00140001).
[ 1641.536191] usb 1-6: new high speed USB device using ehci_hcd and address 6
[ 1641.670365] usb 1-6: configuration #1 chosen from 1 choice
[ 1641.686906] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1641.691934] usb-storage: device found at 6
[ 1641.691937] usb-storage: waiting for device to settle before scanning
[ 1646.690632] usb-storage: device scan complete
[ 1646.691027] scsi 4:0:0:0: Direct-Access     StoreJet  Transcend            PQ: 0 ANSI: 2 CCS
[ 1646.693810] sd 4:0:0:0: Attached scsi generic sg4 type 0
[ 1646.695767] sd 4:0:0:0: [sdd] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[ 1646.696507] sd 4:0:0:0: [sdd] Write Protect is off
[ 1646.696511] sd 4:0:0:0: [sdd] Mode Sense: 34 00 00 00
[ 1646.696514] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[ 1646.698128] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[ 1646.698132]  sdd: sdd1
[ 1646.723380] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[ 1646.723386] sd 4:0:0:0: [sdd] Attached SCSI disk
[ 9420.048861] sd 3:0:0:0: [sdc] 2880 512-byte logical blocks: (1.47 MB/1.40 MiB)
[ 9420.063757] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[ 9420.111757] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[ 9420.111767]  sdc:
ilgaar@ilgaar-laptop:~$

---

### Post by JustinR on 2010-08-12
Nothing really showed up there - sorry! So I guess we can try looking through some programs.

Can you go to System > Administration > Disk Utility and see if the floppy drive is listed? Maybe you can mount it from there.

---

### Post by ilgaar on 2010-08-12
I checked it, it is very odd, it looks like i can format the FDD, but I can't open it! here is the screen shot.

---

### Post by JustinR on 2010-08-12
> **ilgaar said:**
> I checked it, it is very odd, it looks like i can format the FDD, but I can't open it! here is the screen shot.

Okay - it seems that Ubuntu isn't recognizing that the floppy drive is being changed out.

Try installing 'fdflush'. It clears out drive buffers - which should update the status of your floppy drive.

---

### Post by ilgaar on 2010-08-12
Ok, thanks for your help I installed fdflush. but I'm afraid it didn't help, I even tried rebooting, but that didn't helped either. what could be causing the problem?

P.S. It seems I can format the FDD from disk utility, but i can't format it from terminal manually. Am I doing something 
wrong?
By the way when I use fdflush I get this output:

ilgaar@ilgaar-laptop:~$ fdflush
/dev/fd0: No such file or directory.
ilgaar@ilgaar-laptop:~$ fdflush /dev/fd1
/dev/fd1: No such file or directory.
ilgaar@ilgaar-laptop:~$ fdflush /dev/fd2
/dev/fd2: No such file or directory.
ilgaar@ilgaar-laptop:~$ fdflush /dev/fd3
/dev/fd3: No such file or directory.
ilgaar@ilgaar-laptop:~$ fdflush /dev/fd4
/dev/fd4: No such file or directory.
ilgaar@ilgaar-laptop:~$ 

This is odd. the floppy shows up, but it is not mounted? a paradox!

---

### Post by JustinR on 2010-08-12
> **ilgaar said:**
> Ok, thanks for your help I installed fdflush. but I'm afraid it didn't help, I even tried rebooting, but that didn't helped either. what could be causing the problem?

P.S. It seems I can format the FDD from disk utility, but i can't format it from terminal manually. Am I doing something 
wrong?
By the way when I use fdflush I get this output:

ilgaar@ilgaar-laptop:~$ fdflush
/dev/fd0: No such file or directory.
ilgaar@ilgaar-laptop:~$ fdflush /dev/fd1
/dev/fd1: No such file or directory.
ilgaar@ilgaar-laptop:~$ fdflush /dev/fd2
/dev/fd2: No such file or directory.
ilgaar@ilgaar-laptop:~$ fdflush /dev/fd3
/dev/fd3: No such file or directory.
ilgaar@ilgaar-laptop:~$ fdflush /dev/fd4
/dev/fd4: No such file or directory.
ilgaar@ilgaar-laptop:~$ 

This is odd. the floppy shows up, but it is not mounted? a paradox!

Okay. You can uninstall fdflush now (your USB floppy drive is mounted on /dev/sdc and not /dev/fd*).

Could you go into a terminal: Applications > Accessories > Terminal:
```

mount /dev/sdc /mnt

```

---

### Post by ilgaar on 2010-08-12
Ok, thanks, you are right, I missed that, its under /dev/sdc, but when i try to mount it, i get this error:

[HTML]ilgaar@ilgaar-laptop:~$ mount /dev/sdc
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab
ilgaar@ilgaar-laptop:~$[/HTML]

Ans also this is what happens When I try to format it using either fdformat:

[HTML]ilgaar@ilgaar-laptop:~$ sudo fdformat /dev/sdc
Could not determine current format type: Invalid argument
ilgaar@ilgaar-laptop:~$ 
[/HTML]

I can format the floppy by using ufiformat, but I can't open it. I don't understand!

[HTML]ilgaar@ilgaar-laptop:~$ ufiformat /dev/sdc
/dev/sdc: Permission denied
ilgaar@ilgaar-laptop:~$ sudo ufiformat /dev/sdc
geometry: track=80, head=2, sector=18, block=512
done
ilgaar@ilgaar-laptop:~$[/HTML]

---

### Post by ilgaar on 2010-08-12
By the way if i try to mount the floppy i get this output:

[HTML]ilgaar@ilgaar-laptop:~$ sudo mount /dev/sdc /mnt
[sudo] password for ilgaar: 
mount: you must specify the filesystem type
ilgaar@ilgaar-laptop:~$ [/HTML]

filesystem type??

---

### Post by ilgaar on 2010-08-12
Shouldn't opening and mounting a floppy disk be a simple task? Just like opening any other media?

---

### Post by efflandt on 2010-08-12
It is probably best NOT to mount it on /mnt in case something else wants to automount within that directory.  So you should probably create a subdirectory first:

**sudo mkdir /mnt/usb-floppy**

And maybe change permissions so anyone could read/write it (unless you add an fstab entry to allow that).

**sudo chmod 644 /mnt/usb-floppy**

What filesystem did you use when you formatted the floppy?  **man mount** would tell you filesystem types. **-t msdos** is for up to 8.3 character filenames or for long filenames use **-t vfat**.  For example then you could:

**sudo mount -t vfat /dev/sdc /mnt/usb-floppy**

And it may be a good idea to **umount /mnt/usb-floppy** if the system does not recognize if a floppy has been removed or changed.  That was always necessary for any drive (floppies, CD's, etc.) before the age of automounting (including CP/M OS before it became MS-DOS).  My dad brought home a CP/M computer once.  I could mount its 8 inch floppies, but could not figure out how to copy WordStar files on the floppies through a serial port to MS-DOS.

---

### Post by ilgaar on 2010-08-12
Thanks for the help. The problem is the floppy drive is acting very odd. It is detected by the system, the light is flash which means it is working, I checked with a bunch of new diskettes, which means they are OK.
The Floppy Drive is there but it looks like I haven't inserted a diskette in it, which is very odd.

I can't format the disk by fdformat, I get this output:

[HTML]ilgaar@ilgaar-laptop:~$ sudo fdformat /dev/sdc
Could not determine current format type: Invalid argument
ilgaar@ilgaar-laptop:~$[/HTML]

But strangely enough I can format it with ufiformat:

[HTML]ilgaar@ilgaar-laptop:~$ ufiformat /dev/sdc
/dev/sdc: Permission denied
ilgaar@ilgaar-laptop:~$ sudo ufiformat /dev/sdc
geometry: track=80, head=2, sector=18, block=512
done
ilgaar@ilgaar-laptop:~$[/HTML]
---------------------------------------------------------------------
What am I doing wrong? am I not specifying a certain filesystem type?
Do you think I should use another tool to format the FDD? 
---------------------------------------------------------------------
Anyway I tried your suggestion and created a folder, then chmoded it but no luck. this is what I get in the output:

[HTML]ilgaar@ilgaar-laptop:~$ sudo mount -t vfat /dev/sdc /mnt/usb-floppy
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ilgaar@ilgaar-laptop:~$ 
[/HTML]

It's driving me crazy. It has almost took my entire day and yet I haven't been able too fix it. What am I missing?

P.S I tried dmesg and got this:

[HTML][    0.216112] Scanning for low memory corruption every 60 seconds
[    0.216252] audit: initializing netlink socket (disabled)
[    0.216266] type=2000 audit(1281619723.215:1): initialized
[    0.227426] Trying to unpack rootfs image as initramfs...
[    0.240262] highmem bounce pool size: 64 pages
[    0.240269] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.248070] VFS: Disk quotas dquot_6.5.2
[    0.248147] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.248830] fuse init (API version 7.13)
[    0.248922] msgmni has been set to 1690
[    0.249133] alg: No test for stdrng (krng)
[    0.249195] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.249199] io scheduler noop registered
[    0.249201] io scheduler anticipatory registered
[    0.249203] io scheduler deadline registered
[    0.249246] io scheduler cfq registered (default)
[    0.249381]   alloc irq_desc for 24 on node -1
[    0.249384]   alloc kstat_irqs on node -1
[    0.249393] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.249400] pcieport 0000:00:01.0: setting latency timer to 64
[    0.249468] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.249495] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.250057] ACPI: AC Adapter [AC] (on-line)
[    0.250139] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.250682] ACPI: Lid Switch [LID]
[    0.250729] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.250735] ACPI: Power Button [PBTN]
[    0.250784] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.250787] ACPI: Sleep Button [SBTN]
[    0.251221] Marking TSC unstable due to TSC halts in idle
[    0.251274] processor LNXCPU:00: registered as cooling_device0
[    0.259483] Switching to clocksource hpet
[    0.261027] thermal LNXTHERM:01: registered as thermal_zone0
[    0.261036] ACPI: Thermal Zone [THM] (58 C)
[    0.268220] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.268595]   alloc irq_desc for 17 on node -1
[    0.268598]   alloc kstat_irqs on node -1
[    0.268606] serial 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.268613] serial 0000:00:1e.3: PCI INT B disabled
[    0.269636] brd: module loaded
[    0.270128] loop: module loaded
[    0.270220] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.270314] ata_piix 0000:00:1f.2: version 2.13
[    0.270328] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.270334] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.270390] isapnp: Scanning for PnP cards...
[    0.431728] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.436210] scsi0 : ata_piix
[    0.436362] scsi1 : ata_piix
[    0.437195] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.437199] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.437584] Fixed MDIO Bus: probed
[    0.437626] PPP generic driver version 2.4.2
[    0.437704] tun: Universal TUN/TAP device driver, 1.6
[    0.437706] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.437816] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.437844] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.437864] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.437868] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.437908] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.437942] ehci_hcd 0000:00:1d.7: debug port 1
[    0.441841] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.445984] ACPI: Battery Slot [BAT0] (battery present)
[    0.456061] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[    0.468342] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.468500] usb usb1: configuration #1 chosen from 1 choice
[    0.468535] hub 1-0:1.0: USB hub found
[    0.468546] hub 1-0:1.0: 8 ports detected
[    0.468628] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.468648] uhci_hcd: USB Universal Host Controller Interface driver
[    0.468707] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.468718] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.468722] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.468766] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.468796] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    0.468888] usb usb2: configuration #1 chosen from 1 choice
[    0.468915] hub 2-0:1.0: USB hub found
[    0.468925] hub 2-0:1.0: 2 ports detected
[    0.468974] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.468981] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.468985] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.469016] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.469053] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    0.469141] usb usb3: configuration #1 chosen from 1 choice
[    0.469174] hub 3-0:1.0: USB hub found
[    0.469182] hub 3-0:1.0: 2 ports detected
[    0.469226]   alloc irq_desc for 18 on node -1
[    0.469229]   alloc kstat_irqs on node -1
[    0.469236] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.469243] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.469247] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.469280] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.469314] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    0.469413] usb usb4: configuration #1 chosen from 1 choice
[    0.469438] hub 4-0:1.0: USB hub found
[    0.469445] hub 4-0:1.0: 2 ports detected
[    0.469491] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.469498] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.469502] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.469536] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.469568] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    0.469653] usb usb5: configuration #1 chosen from 1 choice
[    0.469682] hub 5-0:1.0: USB hub found
[    0.469689] hub 5-0:1.0: 2 ports detected
[    0.469786] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.476865] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.476877] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.480424] mice: PS/2 mouse device common for all mice
[    0.480585] rtc_cmos 00:06: RTC can wake from S4
[    0.480635] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.480669] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.480802] device-mapper: uevent: version 1.0.3
[    0.480934] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.482227] device-mapper: multipath: version 1.1.0 loaded
[    0.482230] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.483084] EISA: Probing bus 0 at eisa.0
[    0.483092] Cannot allocate resource for EISA slot 1
[    0.483095] Cannot allocate resource for EISA slot 2
[    0.483119] EISA: Detected 0 cards.
[    0.484703] cpuidle: using governor ladder
[    0.484783] cpuidle: using governor menu
[    0.485252] TCP cubic registered
[    0.485427] NET: Registered protocol family 10
[    0.485899] lo: Disabled Privacy Extensions
[    0.486216] NET: Registered protocol family 17
[    0.486505] Using IPI No-Shortcut mode
[    0.486603] PM: Resume from disk failed.
[    0.486615] registered taskstats version 1
[    0.486916]   Magic number: 6:218:483
[    0.487023] rtc_cmos 00:06: setting system clock to 2010-08-12 13:28:44 UTC (1281619724)
[    0.487026] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.487028] EDD information not available.
[    0.487539] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.652577] ata2.00: ATAPI: PIONEER DVD-RW  DVRKD08, 1.00, max UDMA/33
[    0.724041] ata2.00: configured for UDMA/33
[    0.749594] Freeing initrd memory: 7782k freed
[    0.886378] isapnp: No Plug & Play device found
[    0.886614] ata1.00: ATA-6: FUJITSU MHV2100AH, 00000096, max UDMA/100
[    0.886618] ata1.00: 195371568 sectors, multi 8: LBA 
[    0.886634] ata1.00: applying bridge limits
[    0.900714] ata1.00: configured for UDMA/100
[    0.900898] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2100A 0000 PQ: 0 ANSI: 5
[    0.901108] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.901299] sd 0:0:0:0: [sda] 195371568 512-byte logical blocks: (100 GB/93.1 GiB)
[    0.901350] sd 0:0:0:0: [sda] Write Protect is off
[    0.901353] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.901380] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.901555]  sda:
[    0.910602] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVRKD08  1.00 PQ: 0 ANSI: 5
[    0.937780] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.937783] Uniform CD-ROM driver Revision: 3.20
[    0.937883] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.937935] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.974932]  sda1
[    0.975139] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.975156] Freeing unused kernel memory: 660k freed
[    0.975577] Write protecting the kernel text: 4680k
[    0.975616] Write protecting the kernel read-only data: 1840k
[    0.991683] udev: starting version 151
[    1.108077] usb 1-8: new high speed USB device using ehci_hcd and address 5
[    1.230725] ohci1394 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.286044] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dfcfc800-dfcfcfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.293181] b44 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.352104] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.352233] b44.c:v2.0
[    1.372776] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:da:03:83
[    2.564314] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[384fc00038d1dc30]
[    6.244015] usb 1-8: configuration #1 chosen from 1 choice
[    6.253521] Initializing USB Mass Storage driver...
[    6.253630] scsi2 : SCSI emulation for USB Mass Storage devices
[    6.253760] usbcore: registered new interface driver usb-storage
[    6.253763] USB Mass Storage support registered.
[    6.254071] usb-storage: device found at 5
[    6.254073] usb-storage: waiting for device to settle before scanning
[    6.484164] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    6.657438] usb 3-1: configuration #1 chosen from 1 choice
[    6.900167] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    7.086710] usb 4-1: configuration #1 chosen from 1 choice
[    7.093761] scsi3 : SCSI emulation for USB Mass Storage devices
[    7.094054] usb-storage: device found at 2
[    7.094056] usb-storage: waiting for device to settle before scanning
[    7.332167] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    7.504950] usb 5-1: configuration #1 chosen from 1 choice
[    7.542562] usbcore: registered new interface driver hiddev
[    7.542784] usbcore: registered new interface driver usbhid
[    7.542865] usbhid: v2.6:USB HID core driver
[   11.252361] usb-storage: device scan complete
[   11.257751] scsi 2:0:0:0: Direct-Access     ST916082 3AS                   PQ: 0 ANSI: 2
[   11.258532] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   11.259458] sd 2:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[   11.261717] sd 2:0:0:0: [sdb] Write Protect is off
[   11.261721] sd 2:0:0:0: [sdb] Mode Sense: 38 00 00 00
[   11.261724] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   11.264839] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   11.264843]  sdb:
[   12.092049] usb-storage: device scan complete
[   12.110771] scsi 3:0:0:0: Direct-Access     SONY     USB-FDU          6.01 PQ: 0 ANSI: 0 CCS
[   12.111521] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   12.190762] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[   14.155581]  sdb1 sdb2 < sdb5 >
[   14.238811] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   14.238815] sd 2:0:0:0: [sdb] Attached SCSI disk
[   14.438355] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
[   14.438361] EXT4-fs (sdb1): write access will be enabled during recovery
[   16.574294] EXT4-fs (sdb1): recovery complete
[   16.575260] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[   18.150479] Adding 6037496k swap on /dev/sdb5.  Priority:-1 extents:1 across:6037496k 
[   18.508240] udev: starting version 151
[   19.452236] kye 0003:0458:0087.0001: fixing up Kye/Genius Ergo Mouse report descriptor
[   19.455590] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   19.456519] input: Genius Ergo Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input5
[   19.456800] kye 0003:0458:0087.0001: input,hidraw0: USB HID v1.10 Mouse [Genius Ergo Mouse] on usb-0000:00:1d.3-1/input0
[   19.654486] dell-wmi: No known WMI GUID found
[   19.766270] intel_rng: FWH not detected
[   19.783972] Linux agpgart interface v0.103
[   19.925120] type=1505 audit(1281603543.936:2):  operation="profile_load" pid=512 name="/sbin/dhclient3"
[   19.925766] type=1505 audit(1281603543.936:3):  operation="profile_load" pid=512 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.926116] type=1505 audit(1281603543.936:4):  operation="profile_load" pid=512 name="/usr/lib/connman/scripts/dhclient-script"
[   20.484578] Bluetooth: Core ver 2.15
[   20.484682] NET: Registered protocol family 31
[   20.484684] Bluetooth: HCI device and connection manager initialized
[   20.484687] Bluetooth: HCI socket layer initialized
[   20.519800] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   20.520231] usbcore: registered new interface driver btusb
[   20.622834] lib80211: common routines for IEEE802.11 drivers
[   20.622838] lib80211_crypt: registered algorithm 'NULL'
[   20.719855] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   20.719859] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   20.815495] sdhci: Secure Digital Host Controller Interface driver
[   20.815498] sdhci: Copyright(c) Pierre Ossman
[   20.821923] sdhci-pci 0000:03:01.2: SDHCI controller found [1180:0822] (rev 17)
[   20.821945] sdhci-pci 0000:03:01.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[   20.824071] Registered led device: mmc0::
[   20.825156] mmc0: SDHCI controller on PCI [0000:03:01.2] using DMA
[   21.091233] lp: driver loaded but no devices found
[   21.187336] [drm] Initialized drm 1.1.0 20060810
[   21.502157] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input6
[   21.518136] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:20/LNXVIDEO:00/input/input7
[   21.518286] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   21.519046] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   21.519049] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   21.519122] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.532547] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   21.535962] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   21.536059] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
[   21.837550] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[   22.057231] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:0188]
[   22.184793] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[   22.184798] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[   22.184803] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   22.184813] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   22.184818] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[   22.185026] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xdfc00000 - 0xdfcfffff
[   22.185029] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   22.301368] [drm] radeon defaulting to kernel modesetting.
[   22.301372] [drm] radeon kernel modesetting enabled.
[   22.301433] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.301439] radeon 0000:01:00.0: setting latency timer to 64
[   22.303987] [drm] radeon: Initializing kernel modesetting.
[   22.304125] [drm] register mmio base: 0xDFDF0000
[   22.304128] [drm] register mmio size: 65536
[   22.304473] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   22.304495] [drm] Generation 2 PCI interface, using max accessible memory
[   22.304499] [drm] radeon: VRAM 128M
[   22.304501] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   22.304503] [drm] radeon: GTT 512M
[   22.304505] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[   22.304539]   alloc irq_desc for 25 on node -1
[   22.304542]   alloc kstat_irqs on node -1
[   22.304555] radeon 0000:01:00.0: irq 25 for MSI/MSI-X
[   22.304561] [drm] radeon: using MSI.
[   22.304591] [drm] radeon: irq initialized.
[   22.305619] [drm] Detected VRAM RAM=128M, BAR=128M
[   22.305623] [drm] RAM width 128bits DDR
[   22.305749] [TTM] Zone  kernel: Available graphics memory: 436944 kiB.
[   22.305752] [TTM] Zone highmem: Available graphics memory: 1030778 kiB.
[   22.305775] [drm] radeon: 128M of VRAM memory ready
[   22.305777] [drm] radeon: 512M of GTT memory ready.
[   22.305982] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   22.306526] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   22.306565] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   22.306576] [drm] radeon: cp idle (0x10000C03)
[   22.306689] [drm] Loading R300 Microcode
[   22.306991] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   22.338277] [drm] radeon: ring at 0x0000000020000000
[   22.338303] [drm] ring test succeeded in 1 usecs
[   22.338466] [drm] radeon: ib pool ready.
[   22.338538] [drm] ib test succeeded in 0 usecs
[   22.338639] [drm] Panel ID String: DD282154X3
[   22.338640]             
[   22.338642] [drm] Panel Size 1280x800
[   22.338678] [drm] Default TV standard: NTSC
[   22.338680] [drm] 27.000000000 MHz TV ref clk
[   22.338683] [drm] Default TV standard: NTSC
[   22.338685] [drm] 27.000000000 MHz TV ref clk
[   22.338713] [drm] Radeon Display Connectors
[   22.338715] [drm] Connector 0:
[   22.338717] [drm]   VGA
[   22.338720] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   22.338722] [drm]   Encoders:
[   22.338724] [drm]     CRT1: INTERNAL_DAC1
[   22.338725] [drm] Connector 1:
[   22.338727] [drm]   LVDS
[   22.338728] [drm]   Encoders:
[   22.338730] [drm]     LCD1: INTERNAL_LVDS
[   22.338732] [drm] Connector 2:
[   22.338734] [drm]   S-video
[   22.338735] [drm]   Encoders:
[   22.338737] [drm]     TV1: INTERNAL_DAC2
[   22.370397] [drm] fb mappable at 0xD00C0000
[   22.370400] [drm] vram apper at 0xD0000000
[   22.370402] [drm] size 4096000
[   22.370403] [drm] fb depth is 24
[   22.370405] [drm]    pitch is 5120
[   22.371104] fb0: radeondrmfb frame buffer device
[   22.371106] registered panic notifier
[   22.371114] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   22.435356] hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
[   22.435363] Disabling lock debugging due to kernel taint
[   22.675666] hsfich 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   22.711756] vga16fb: initializing
[   22.711761] vga16fb: mapped to 0xc00a0000
[   22.711765] vga16fb: not registering due to another framebuffer present
[   22.887355] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   22.889127] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   22.889858] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   22.890462] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   22.891236] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   23.390287] Console: switching to colour frame buffer device 160x50
[   26.822464] type=1505 audit(1281603550.832:5):  operation="profile_load" pid=867 name="/usr/share/gdm/guest-session/Xsession"
[   26.824326] type=1505 audit(1281603550.836:6):  operation="profile_replace" pid=868 name="/sbin/dhclient3"
[   26.824976] type=1505 audit(1281603550.836:7):  operation="profile_replace" pid=868 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   26.825328] type=1505 audit(1281603550.836:8):  operation="profile_replace" pid=868 name="/usr/lib/connman/scripts/dhclient-script"
[   27.048232] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.504221] type=1505 audit(1281603551.516:9):  operation="profile_load" pid=869 name="/usr/bin/evince"
[   27.512719] type=1505 audit(1281603551.524:10):  operation="profile_load" pid=869 name="/usr/bin/evince-previewer"
[   27.517982] type=1505 audit(1281603551.528:11):  operation="profile_load" pid=869 name="/usr/bin/evince-thumbnailer"
[   27.735681] hsfich 0000:00:1e.3: setting latency timer to 64
[   27.744915] type=1505 audit(1281603551.756:12):  operation="profile_load" pid=943 name="/usr/bin/freshclam"
[   27.760875] type=1505 audit(1281603551.772:13):  operation="profile_load" pid=945 name="/usr/sbin/clamd"
[   27.766282] type=1505 audit(1281603551.776:14):  operation="profile_load" pid=946 name="/usr/lib/cups/backend/cups-pdf"
[   28.152238] ttySHSF0 at I/O 0xee00 (irq = 17) is a Conexant HSF softmodem (PCI-8086:266d-14f1:5423)
[   28.152729] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.152774] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   28.178231] NET: Registered protocol family 15
[   28.315357] alg: No test for cipher_null (cipher_null-generic)
[   28.315395] alg: No test for ecb(cipher_null) (ecb-cipher_null)
[   28.315423] alg: No test for digest_null (digest_null-generic)
[   28.315449] alg: No test for compress_null (compress_null-generic)
[   28.505532] padlock: VIA PadLock Hash Engine not detected.
[   28.590635] padlock: VIA PadLock Hash Engine not detected.
[   28.772290] padlock: VIA PadLock not detected.
[   28.980045] intel8x0_measure_ac97_clock: measured 55423 usecs (2670 samples)
[   28.980049] intel8x0: clocking to 48000
[   29.816186] b44: eth0: Link is up at 100 Mbps, full duplex.
[   29.816189] b44: eth0: Flow control is off for TX and off for RX.
[   29.816473] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.804819] intel_rng: FWH not detected
[   31.506607] Initializing XFRM netlink socket
[   31.510949] padlock: VIA PadLock not detected.
[   31.514547] padlock: VIA PadLock Hash Engine not detected.
[   31.519751] padlock: VIA PadLock not detected.
[   33.440062] hsfich 0000:00:1e.3: PCI INT B disabled
[   33.795176] hsfich 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   33.865977] hsfich 0000:00:1e.3: setting latency timer to 64
[   34.288258] ttySHSF0 at I/O 0xee00 (irq = 17) is a Conexant HSF softmodem (PCI-8086:266d-14f1:5423)
[   34.758374] usbcore: registered new interface driver hsfusbcd2
[   37.612015] eth1: no IPv6 routers present
[   40.576029] eth0: no IPv6 routers present
[   50.506383] tun0: Disabled Privacy Extensions
[   52.114654] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   52.114659] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   52.114661] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   52.114662] vboxdrv: the usage of hardware performance counters by
[   52.114664] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   52.114668] vboxdrv: Found 1 processor cores.
[   52.116765] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   52.116769] vboxdrv: Successfully loaded version 3.2.8 (interface 0x00140001).
[   53.921050] Bluetooth: L2CAP ver 2.14
[   53.921054] Bluetooth: L2CAP socket layer initialized
[   54.002526] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   54.002530] Bluetooth: BNEP filters: protocol multicast
[   54.035498] Bridge firewalling registered
[   54.403926] Bluetooth: SCO (Voice Link) ver 0.6
[   54.403930] Bluetooth: SCO socket layer initialized
[   55.467827] Bluetooth: RFCOMM TTY layer initialized
[   55.467832] Bluetooth: RFCOMM socket layer initialized
[   55.467835] Bluetooth: RFCOMM ver 1.11
[   87.491743] sd 3:0:0:0: [sdc] 2880 512-byte logical blocks: (1.47 MB/1.40 MiB)
[   87.507746] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   87.555753] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   87.555760]  sdc: [mac] sdc1 sdc2
[  159.796752] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  159.796764]  sdc: unknown partition table
[  190.144925] __ratelimit: 6 callbacks suppressed
[  190.144936] operapluginwrap[2686]: segfault at 0 ip (null) sp bfcf466c error 4 in libdl-2.11.1.so[110000+2000]
[  190.187632] operapluginwrap[2688]: segfault at 0 ip (null) sp bf966f5c error 4 in libm-2.11.1.so[110000+24000]
[  190.251487] operapluginwrap[2690]: segfault at 0 ip (null) sp bfb7170c error 4 in libstdc++.so.6.0.13[110000+e9000]
[  190.283746] operapluginwrap[2691]: segfault at 0 ip (null) sp bffbeb1c error 4 in libXt.so.6.0.0[110000+4f000]
[  190.295399] operapluginwrap[2692]: segfault at 0 ip (null) sp bf9812dc error 4 in libdl-2.11.1.so[110000+2000]
[  190.303391] operapluginwrap[2693]: segfault at 0 ip (null) sp bfbd29bc error 4 in libstdc++.so.6.0.13[110000+e9000]
[  190.314550] operapluginwrap[2695]: segfault at 0 ip (null) sp bfa32a3c error 4
[  190.321402] operapluginwrap[2696]: segfault at 0 ip (null) sp bfd4b0bc error 4 in libX11.so.6.3.0[110000+119000]
[ 5848.140944] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[17904.456062] usb 1-6: new high speed USB device using ehci_hcd and address 6
[17904.589276] usb 1-6: configuration #1 chosen from 1 choice
[17904.590544] scsi4 : SCSI emulation for USB Mass Storage devices
[17904.591312] usb-storage: device found at 6
[17904.591317] usb-storage: waiting for device to settle before scanning
[17909.588920] usb-storage: device scan complete
[17909.589421] scsi 4:0:0:0: Direct-Access     StoreJet  Transcend            PQ: 0 ANSI: 2 CCS
[17909.594541] sd 4:0:0:0: Attached scsi generic sg4 type 0
[17909.595625] sd 4:0:0:0: [sdd] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[17909.596628] sd 4:0:0:0: [sdd] Write Protect is off
[17909.596636] sd 4:0:0:0: [sdd] Mode Sense: 34 00 00 00
[17909.596643] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[17909.598241] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[17909.598249]  sdd: sdd1
[17909.625497] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[17909.625508] sd 4:0:0:0: [sdd] Attached SCSI disk
[18025.006967] PPP MPPE Compression module registered
[32447.579204] sd 3:0:0:0: [sdc] 2880 512-byte logical blocks: (1.47 MB/1.40 MiB)
[32447.595197] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[32447.644182] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[32447.644194]  sdc: unknown partition table
[32854.600715] FAT: invalid media value (0xf6)
[32854.600725] VFS: Can't find a valid FAT filesystem on dev sdc.
[32929.018824] FAT: invalid media value (0xf6)
[32929.018834] VFS: Can't find a valid FAT filesystem on dev sdc.
[33478.012925] FAT: invalid media value (0xf6)
[33478.012934] VFS: Can't find a valid FAT filesystem on dev sdc.
ilgaar@ilgaar-laptop:~$ 
[/HTML]

What the...?

---

