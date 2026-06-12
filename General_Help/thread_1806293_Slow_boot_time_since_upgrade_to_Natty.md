---
title: "Slow boot time since upgrade to Natty"
date: 2011-07-17
forum: General Help
---

### Post by coeus82 on 2011-07-17
Hello, I've seen this issue mentioned before, but it appears their cause was different than mine. 

Here is a snippet of my dmesg log:

```

[    2.797917] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.798077] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.798149] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    3.000059] usb 2-6: new full speed USB device using ohci_hcd and address 3
[    3.118305] ata6: SATA link down (SStatus 0 SControl 300)
[    3.125541] Initializing USB Mass Storage driver...
[    3.125729] scsi6 : usb-storage 1-3:1.0
[    3.125993] usbcore: registered new interface driver usb-storage
[    3.125995] USB Mass Storage support registered.
[    3.156139] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input2
[    3.156257] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-4/input0
[    3.165077] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    3.165638] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/input/input3
[    3.165813] logitech 0003:046D:C517.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-4/input1
[    3.226170] input: HP HP Digital Stereo Headset as /devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.3/input/input4
[    3.226269] generic-usb 0003:03F0:8C07.0003: input,hidraw2: USB HID v1.00 Device [HP HP Digital Stereo Headset] on usb-0000:00:02.0-6/input3
[    3.386594] EXT4-fs (sda3): INFO: recovery required on readonly filesystem
[    3.386598] EXT4-fs (sda3): write access will be enabled during recovery
[    4.124693] scsi 6:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS
[    4.125192] scsi 6:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0
[    4.125782] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    4.127562] sd 6:0:0:0: [sdb] 15695871 512-byte logical blocks: (8.03 GB/7.48 GiB)
[    4.128684] sd 6:0:0:0: [sdb] Write Protect is off
[    4.128689] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[    4.128691] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.129311] sr1: scsi3-mmc drive: 48x/48x tray
[    4.129481] sr 6:0:0:1: Attached scsi CD-ROM sr1
[    4.129578] sr 6:0:0:1: Attached scsi generic sg3 type 5
[    4.131421] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.132404]  sdb: sdb1
[    4.134512] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.134516] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    5.818145] EXT4-fs (sda3): orphan cleanup on readonly fs
[    5.818155] EXT4-fs (sda3): ext4_orphan_cleanup: deleting unreferenced inode 2752526
[    5.818178] EXT4-fs (sda3): ext4_orphan_cleanup: deleting unreferenced inode 2752525
[    5.818184] EXT4-fs (sda3): ext4_orphan_cleanup: deleting unreferenced inode 2752524
[    5.818191] EXT4-fs (sda3): ext4_orphan_cleanup: deleting unreferenced inode 2752523
[    5.818196] EXT4-fs (sda3): ext4_orphan_cleanup: deleting unreferenced inode 2752522
[    5.818201] EXT4-fs (sda3): 5 orphan inodes deleted
[    5.818203] EXT4-fs (sda3): recovery complete
[    6.066029] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    8.239800] Adding 3904508k swap on /dev/sda5.  Priority:-1 extents:1 across:3904508k 
[    9.597273] <30>udev[390]: starting version 167
[   11.510641] lp: driver loaded but no devices found
[   11.518279] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
[   11.518305] i2c i2c-1: nForce2 SMBus adapter at 0x4e00
[   11.626170] parport_pc 00:06: reported by Plug and Play ACPI
[   11.626216] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.720232] lp0: using parport0 (interrupt-driven).
[   12.005386] ppdev: user-space parallel port driver
[   12.268230] type=1400 audit(1310921903.127:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=634 comm="apparmor_parser"
[   12.268269] type=1400 audit(1310921903.127:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=536 comm="apparmor_parser"
[   12.268575] type=1400 audit(1310921903.127:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=634 comm="apparmor_parser"
[   12.268615] type=1400 audit(1310921903.127:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=536 comm="apparmor_parser"
[   12.268797] type=1400 audit(1310921903.127:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=634 comm="apparmor_parser"
[   12.268842] type=1400 audit(1310921903.127:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
[   12.838384] nvidia: module license 'NVIDIA' taints kernel.
[   12.838388] Disabling lock debugging due to kernel taint
[   13.360380] nvidia 0000:00:0d.0: enabling device (0000 -> 0002)
[   13.360583] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 23
[   13.360589] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 23 (level, low) -> IRQ 23
[   13.360597] nvidia 0000:00:0d.0: setting latency timer to 64
[   13.360602] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=io+mem,decodes=none:owns=none
[   13.360922] ACPI: PCI Interrupt Link [LNED] enabled at IRQ 18
[   13.360938] nvidia 0000:02:00.0: PCI INT A -> Link[LNED] -> GSI 18 (level, low) -> IRQ 18
[   13.360942] nvidia 0000:02:00.0: setting latency timer to 64
[   13.360945] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.361124] NVRM: loading NVIDIA UNIX x86 Kernel Module  275.19  Tue Jul 12 18:29:18 PDT 2011
[   13.560509] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   13.560518] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   13.560522] hda_intel: Disable MSI for Nvidia chipset
[   13.560552] HDA Intel 0000:00:05.0: setting latency timer to 64
[   13.575597] usbcore: registered new interface driver snd-usb-audio
[   14.456057] hda_codec: ALC888: BIOS auto-probing.
[   15.016341] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input5
[   15.016465] HDA Intel 0000:02:00.1: PCI INT A -> Link[LNED] -> GSI 18 (level, low) -> IRQ 18
[   15.016469] hda_intel: Disable MSI for Nvidia chipset
[   15.016517] HDA Intel 0000:02:00.1: setting latency timer to 64
[   56.054309] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   57.850831] type=1400 audit(1310921948.707:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=5483 comm="apparmor_parser"
[   57.851203] type=1400 audit(1310921948.707:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=5483 comm="apparmor_parser"
[   57.851446] type=1400 audit(1310921948.707:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=5483 comm="apparmor_parser"
[   57.985561] type=1400 audit(1310921948.843:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=5482 comm="apparmor_parser"
[   58.252124] type=1400 audit(1310921949.111:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=5501 comm="apparmor_parser"
[   58.252549] type=1400 audit(1310921949.111:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=5501 comm="apparmor_parser"
[   58.354867] type=1400 audit(1310921949.211:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=5533 comm="apparmor_parser"
[   58.549546] type=1400 audit(1310921949.407:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=5544 comm="apparmor_parser"
[   58.581771] type=1400 audit(1310921949.439:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=5484 comm="apparmor_parser"
[   58.586430] type=1400 audit(1310921949.443:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=5484 comm="apparmor_parser"
[   59.316424] r8169 0000:04:00.0: eth0: link down
[   59.316433] r8169 0000:04:00.0: eth0: link down
[   59.316681] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

It looks like the issue is here:

> 
[   15.016517] HDA Intel 0000:02:00.1: setting latency timer to 64
[   56.054309] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro


I'm not exactly sure what that is or why that's causing it to take so long to do. Can anyone help?

---

### Post by coeus82 on 2011-07-19
anyone?

---

### Post by 2F4U on 2011-07-20
I am unable to see a problem in the to lines you highlighted. The first seems to be related to the graphics card and the second most likely remounts the root partition. However, at the end of your dmesg output it says that eth0 is not ready and this is related to the network connection.

---

