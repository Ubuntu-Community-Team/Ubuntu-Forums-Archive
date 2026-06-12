---
title: "USB drives not found after a safe disconnect"
date: 2009-11-14
forum: General Help
---

### Post by Jabb3r on 2009-11-14
Hi there guys, bit of a strange one. I'll post as much info as I know howto. Anyway I have 3 usb drives attatched to a logitech 4 port hub (2x external hdd and a 4Gb pen drive. When I connect them all and plug hub in everything works fine, all 3 drives are mounted and are fully accessible etc. If however I safely remove a drive and then plug it back in the drive doesn't seem to be mounted unless I remove hub, plug in pen drive and plug hub back in, then all is found and working fine again. I did think that it could be a hub problem, but I tried connecting to another usb port on the system and ecactly the same thing happens. The activity l.e.d on drive does flash so theres some communication going on as the logs should proove. I'm on Ubuntu 9.10

I'll use the 4Gb verbatim pen drive as the example as thats the one I'm more likely to remove.

Working
dmesg
*******

[ 8572.248018] usb 1-5: new high speed USB device using ehci_hcd and address 19
[ 8572.380530] usb 1-5: configuration #1 chosen from 1 choice
[ 8572.382238] hub 1-5:1.0: USB hub found
[ 8572.382336] hub 1-5:1.0: 4 ports detected
[ 8572.676146] usb 1-5.1: new high speed USB device using ehci_hcd and address 20
[ 8572.795367] usb 1-5.1: configuration #1 chosen from 1 choice
[ 8572.796326] scsi15 : SCSI emulation for USB Mass Storage devices
[ 8572.796454] usb-storage: device found at 20
[ 8572.796456] usb-storage: waiting for device to settle before scanning
[ 8572.884129] usb 1-5.3: new high speed USB device using ehci_hcd and address 21
[ 8572.992974] usb 1-5.3: configuration #1 chosen from 1 choice
[ 8572.994797] scsi16 : SCSI emulation for USB Mass Storage devices
[ 8572.995057] usb-storage: device found at 21
[ 8572.995060] usb-storage: waiting for device to settle before scanning
[ 8577.796274] usb-storage: device scan complete
[ 8577.828004] scsi 15:0:0:0: Direct-Access     Verbatim STORE N GO       5.00 PQ: 0 ANSI: 0 CCS
[ 8577.828539] sd 15:0:0:0: Attached scsi generic sg3 type 0
[ 8577.992143] usb-storage: device scan complete
[ 8578.045368] scsi 16:0:0:0: Direct-Access     Maxtor   OneTouch II      023g PQ: 0 ANSI: 4
[ 8578.045887] sd 16:0:0:0: Attached scsi generic sg4 type 0
[ 8578.070085] sd 15:0:0:0: [sdc] 7827456 512-byte logical blocks: (4.00 GB/3.73 GiB)
[ 8578.070578] sd 15:0:0:0: [sdc] Write Protect is off
[ 8578.070582] sd 15:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 8578.070585] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[ 8578.074704] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[ 8578.074712]  sdc:
[ 8578.108966] sd 16:0:0:0: [sdd] 398297088 512-byte logical blocks: (203 GB/189 GiB)
[ 8578.118097]  sdc1
[ 8578.124840] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[ 8578.124849] sd 15:0:0:0: [sdc] Attached SCSI removable disk
[ 8578.162587] sd 16:0:0:0: [sdd] Write Protect is off
[ 8578.162593] sd 16:0:0:0: [sdd] Mode Sense: 24 00 00 00
[ 8578.162597] sd 16:0:0:0: [sdd] Assuming drive cache: write through
[ 8578.269570] sd 16:0:0:0: [sdd] Assuming drive cache: write through
[ 8578.269577]  sdd: sdd1
[ 8578.406701] sd 16:0:0:0: [sdd] Assuming drive cache: write through
[ 8578.406710] sd 16:0:0:0: [sdd] Attached SCSI disk
[ 8586.024138] usb 1-5.4: new high speed USB device using ehci_hcd and address 22
[ 8586.133103] usb 1-5.4: configuration #1 chosen from 1 choice
[ 8586.133339] scsi17 : SCSI emulation for USB Mass Storage devices
[ 8586.133467] usb-storage: device found at 22
[ 8586.133469] usb-storage: waiting for device to settle before scanning
[ 8591.132146] usb-storage: device scan complete
[ 8591.132618] scsi 17:0:0:0: Direct-Access     Maxtor   Basics Desktop   0122 PQ: 0 ANSI: 4
[ 8591.133114] sd 17:0:0:0: Attached scsi generic sg5 type 0
[ 8591.145596] sd 17:0:0:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[ 8591.146214] sd 17:0:0:0: [sde] Write Protect is off
[ 8591.146219] sd 17:0:0:0: [sde] Mode Sense: 2d 08 00 00
[ 8591.146222] sd 17:0:0:0: [sde] Assuming drive cache: write through
[ 8591.147588] sd 17:0:0:0: [sde] Assuming drive cache: write through
[ 8591.147593]  sde: sde1
[ 8591.183859] sd 17:0:0:0: [sde] Assuming drive cache: write through
[ 8591.183867] sd 17:0:0:0: [sde] Attached SCSI disk
jabb3r@Earth:~$

Disconnected pen drive
**********************

[10153.065319] pidgin[1899]: segfault at a ip 005210fc sp bf828360 error 4 in libc-2.10.1.so[4b6000+13e000]
[10287.088111] usb 1-5.4: reset high speed USB device using ehci_hcd and address 22
[13279.088068] usb 1-5.4: reset high speed USB device using ehci_hcd and address 22
[13283.433239] usb 1-5.1: USB disconnect, address 20

Reconnect pen drive (not working)
*********************************

[13353.528189] usb 1-5.1: new high speed USB device using ehci_hcd and address 23
[13353.647286] usb 1-5.1: configuration #1 chosen from 1 choice
[13353.648110] scsi18 : SCSI emulation for USB Mass Storage devices
[13353.648240] usb-storage: device found at 23
[13353.648243] usb-storage: waiting for device to settle before scanning
[13358.648319] usb-storage: device scan complete
[13358.680051] scsi 18:0:0:0: Direct-Access     Verbatim STORE N GO       5.00 PQ: 0 ANSI: 0 CCS
[13358.680568] sd 18:0:0:0: Attached scsi generic sg3 type 0
[13361.650594] sd 18:0:0:0: [sdc] 7827456 512-byte logical blocks: (4.00 GB/3.73 GiB)
[13361.651085] sd 18:0:0:0: [sdc] Write Protect is off
[13361.651089] sd 18:0:0:0: [sdc] Mode Sense: 23 00 00 00
[13361.651092] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[13361.655085] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[13361.655092]  sdc: sdc1
[13361.702705] sd 18:0:0:0: [sdc] Assuming drive cache: write through
[13361.702713] sd 18:0:0:0: [sdc] Attached SCSI removable disk

sudo fdisk -lu
**************

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2de12de0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   115330634    57665286    7  HPFS/NTFS
/dev/sda2       115330635   156296384    20482875    5  Extended
/dev/sda5       115330698   154497104    19583203+  83  Linux
/dev/sda6       154497168   156296384      899608+  82  Linux swap / Solaris

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9503c6ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   398283479   199141708+   c  W95 FAT32 (LBA)

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7aff0e96

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  1953520064   976760001    7  HPFS/NTFS

Disk /dev/sdc: 4007 MB, 4007657472 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0027e3ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     7827455     3913696+   7  HPFS/NTFS
Partition 1 has different physical/logical endings:
     phys=(486, 254, 63) logical=(487, 60, 21)

ls usb
******

Bus 003 Device 003: ID 0a48:3260 I/O Interconnect 
Bus 003 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 023: ID 13fe:1e23 Kingston Technology Company Inc. 
Bus 001 Device 022: ID 0d49:7410 Maxtor 
Bus 001 Device 021: ID 0d49:7110 Maxtor 
Bus 001 Device 019: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Not seeing the verb pen drive here. I do have an 8Gb kingston one, but it wasn't attatched @ the time I took these logs. :S

Thanks
Jabb3r

---

### Post by Jabb3r on 2009-11-14
Just wanted to add that when the pen drive isn't plugged in the Kingston entry doesn't appear on lsusb.

---

### Post by Jabb3r on 2009-11-17
Still havin same prob, any ideas guys?

---

