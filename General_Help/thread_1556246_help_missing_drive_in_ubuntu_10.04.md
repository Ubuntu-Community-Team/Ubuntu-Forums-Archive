---
title: "help: missing drive in ubuntu 10.04"
date: 2010-08-19
forum: General Help
---

### Post by zissshh on 2010-08-19
pls help me solve this
       i was downloading some media into the user default downloads folder,after checking completed downloads the system went weird ,,when clicked on the download folder it skipped back to the file system and when i browsed back the media drive where it was supposed tio be copied and stored, it went missing the whole drive ,,can you help me recover the drive ,i restarted the system,is wine also responsible for such weird act,i also uninstalled it but its still in the applications,pls help:D

---

### Post by zaphod777 on 2010-08-19
If it is a USB drive have you tried disconnecting it and reconnecting it? Also make sure that the power to the drive is connected. 

Once you reconnect the drive in the terminal type
```
dmesg
```
and post the last 10-20 lines or so that will give us a clue as to what is going on.

---

### Post by zissshh on 2010-08-19
now its not a usb its my hardrive

[    2.292781] sd 0:0:0:0: [sda] Write Protect is off
[    2.292784] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.292807] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.293235]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
[    2.361358] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.614288] ata2: SATA link down (SStatus 0 SControl 300)
[    2.615271] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S222A  ID00 PQ: 0 ANSI: 5
[    2.619047] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.619052] Uniform CD-ROM driver Revision: 3.20
[    2.619189] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.619262] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.619397] ata4: port disabled. ignoring.
[    2.878357] kjournald starting.  Commit interval 5 seconds
[    2.878369] EXT3-fs: mounted filesystem with ordered data mode.
[    2.942311] ata6: SATA link down (SStatus 0 SControl 300)
[   22.119219] udev: starting version 151
[   22.158978] Adding 1951824k swap on /dev/sda8.  Priority:-1 extents:1 across:1951824k 
[   22.215835] i2c i2c-0: nForce2 SMBus adapter at 0x600
[   22.215859] i2c i2c-1: nForce2 SMBus adapter at 0x700
[   22.241904] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   22.326257] lp: driver loaded but no devices found
[   22.347730] vga16fb: initializing
[   22.347735] vga16fb: mapped to 0xc00a0000
[   22.347810] fb0: VGA16 VGA frame buffer device
[   22.385162] parport_pc 00:06: reported by Plug and Play ACPI
[   22.385210] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   22.408327] Linux agpgart interface v0.103
[   22.457130] nvidia: module license 'NVIDIA' taints kernel.
[   22.457136] Disabling lock debugging due to kernel taint
[   22.464348] type=1505 audit(1282202836.972:2):  operation="profile_load" pid=613 name="/sbin/dhclient3"
[   22.464633] type=1505 audit(1282202836.972:3):  operation="profile_load" pid=613 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   22.464793] type=1505 audit(1282202836.972:4):  operation="profile_load" pid=613 name="/usr/lib/connman/scripts/dhclient-script"
[   22.479577] lp0: using parport0 (interrupt-driven).
[   22.656181] psmouse serio1: ID: 10 00 64
[   23.303535] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   23.575256] ppdev: user-space parallel port driver
[   23.704789] EXT3 FS on sda1, internal journal
[   23.807900] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   23.807907] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   23.807911] hda_intel: Disable MSI for Nvidia chipset
[   23.807939] HDA Intel 0000:00:05.0: setting latency timer to 64
[   23.857943] Console: switching to colour frame buffer device 80x30
[   24.293242] type=1505 audit(1282202838.800:5):  operation="profile_load" pid=764 name="/usr/share/gdm/guest-session/Xsession"
[   24.295107] type=1505 audit(1282202838.800:6):  operation="profile_replace" pid=765 name="/sbin/dhclient3"
[   24.295406] type=1505 audit(1282202838.800:7):  operation="profile_replace" pid=765 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   24.295572] type=1505 audit(1282202838.800:8):  operation="profile_replace" pid=765 name="/usr/lib/connman/scripts/dhclient-script"
[   24.299544] type=1505 audit(1282202838.804:9):  operation="profile_load" pid=766 name="/usr/bin/evince"
[   24.303349] type=1505 audit(1282202838.808:10):  operation="profile_load" pid=766 name="/usr/bin/evince-previewer"
[   24.305754] type=1505 audit(1282202838.812:11):  operation="profile_load" pid=766 name="/usr/bin/evince-thumbnailer"
[   24.396169] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input5
[   24.540739] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 21
[   24.540748] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 21 (level, low) -> IRQ 21
[   24.540756] nvidia 0000:00:0d.0: setting latency timer to 64
[   24.540761] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   24.541050] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   24.593480]   alloc irq_desc for 27 on node -1
[   24.593485]   alloc kstat_irqs on node -1
[   24.593495] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X
[   24.638292] NET: Registered protocol family 24
[   34.884026] eth0: no IPv6 routers present
[   87.664033] Clocksource tsc unstable (delta = -211526317 ns)

---

### Post by zaphod777 on 2010-08-19
can you post the results of 
```
cat /etc/fstab
```

I want to see what your HDD is set as.

How many HDD do you have 2?

---

### Post by zissshh on 2010-08-19
i have a single hitachi 


sudhir@sudhir-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda1 during installation
UUID=294ca413-fbad-40bf-81e0-7c328d0e997a  /            ext3  errors=remount-ro        0  1  
# swap was on /dev/sda8 during installation
UUID=ac454a83-e2dc-4ba4-86c8-1e56fa69c88a  none         swap  sw                       0  0  
/dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,umask=000  0  0  
/dev/sda7                                  /media/sda7  ntfs  nls=iso8859-1,umask=000  0  0

---

### Post by zissshh on 2010-08-20
HELP  iam brimming on the edge of losing it :(
[SIZE=7]HELP[/SIZE]

---

### Post by zissshh on 2011-08-26
i some how managed to retrieve the data and change my system,,,also the old system is working fine minus the data,,,i retrived the data using live cd,,,
  the old system is fine as i reloaded it with xp,,,,as it was not able to read the live cd

thanks to all:)

sorry for the late post

---

