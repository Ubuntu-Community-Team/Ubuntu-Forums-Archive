---
title: "bloody flash drives"
date: 2006-04-05
forum: General Help
---

### Post by ntbutler on 2006-04-05
Hey. I am relatively new to ubuntu, but not that bad at it.
I had ubuntu 5.04 installed, and everything was working fine.
I recently upgraded to 5.10, but now i cannot mount my usb drive. It still works on windows machines at uni, but not on ubuntu.

here is the dmesg when i attatch the flash drive.

> [4296074.118000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[4296075.018000] SCSI subsystem initialized
[4296075.052000] Initializing USB Mass Storage driver...
[4296075.059000] scsi0 : SCSI emulation for USB Mass Storage devices
[4296075.064000] usb-storage: device found at 3
[4296075.064000] usb-storage: waiting for device to settle before scanning
[4296075.064000] usbcore: registered new driver usb-storage
[4296075.065000] USB Mass Storage support registered.


The system ->preferences crap says it should automatically mount and display on my desktop, but it doesnt.

When i remove the drive, i get this (i am not sure if it will help at all)
>  usb 2-1: USB disconnect, address 4


When i attatched the drive again, i got this:
[> 4296795.118000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[4296795.221000] scsi1 : SCSI emulation for USB Mass Storage devices
[4296795.225000] usb-storage: device found at 4
[4296795.225000] usb-storage: waiting for device to settle before scanning
[4296796.115000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296796.115000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296796.199000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296796.199000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296799.037000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296799.037000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296799.154000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296799.154000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296800.229000]   Vendor: SanDisk   Model: Cruzer Micro      Rev: 0.2
[4296800.229000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4296800.241000] SCSI device sda: 1000944 512-byte hdwr sectors (512 MB)
[4296800.246000] sda: Write Protect is off
[4296800.246000] sda: Mode Sense: 03 00 00 00
[4296800.246000] sda: assuming drive cache: write through
[4296800.265000] SCSI device sda: 1000944 512-byte hdwr sectors (512 MB)
[4296800.270000] sda: Write Protect is off
[4296800.270000] sda: Mode Sense: 03 00 00 00
[4296800.270000] sda: assuming drive cache: write through
[4296800.270000]  /dev/scsi/host1/bus0/target0/lun0: p1
[4296800.282000] Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
[4296800.287000] usb-storage: device scan complete


as you can see, i am getting alot of this crap:
> [4296776.631000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296776.631000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.


anyone got any ideas?

---

### Post by encompass on 2006-04-05
Have you tried manually mounting with sudo?
I had some similar issues, check to make sure you have permissions to mount devices.  This is found in the systems menu and users, and groups.  I could mount my cdrom either.
Hope that helps.

---

### Post by ntbutler on 2006-04-05
yeah, i have the permissions, but when i try using 
sudo mount -vfat /media/usb
or
sudo mount -vfat /media/usb0
or
sudo mount -vfat /dev/sda1
(as far as i can tell these are the usb points), nothing happens, it just says "nothing was mounted".
Have i got my command wrong?
thanx 4 the quick reply.

---

### Post by encompass on 2006-04-05
tye sda*
or it could be the disk is bad, as in it works in others cause they are not picky about partitions but linux is... you could format it in windows to fat32 again and see if that fixes the issue. But that is just a swing, whether it helps, I highly doubt it.:???:

---

### Post by dcstar on 2006-04-05
[QUOTE=ntbutler]
.......
as you can see, i am getting alot of this crap:

anyone got any ideas?[/QUOTE]
Please ask questions about different problems in different posts:

[http://ubuntuforums.org/showthread.php?t=119499](http://ubuntuforums.org/showthread.php?t=119499)

---

