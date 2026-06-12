---
title: "USB External Drive (ext3) Randomly Un-mounts"
date: 2010-07-21
forum: General Help
---

### Post by sharkllama on 2010-07-21
Hi, 
   I have a Seagate USB external drive that functioned perfectly when I was using Ubuntu 9.10.  Upon upgrading to ubuntu 10.4 the drive will randomly unmount itself and is no longer visible to the system (I search for it using fdisk -l), so there is no way to re-mount the drive.  The output of dmesg is shown below

[email]sharkllama@quaaludes:~/.unison[/email]$ dmesg | tail
[429521.983716] usb 2-1: USB disconnect, address 7
[429522.341654] usb 2-1: new high speed USB device using ehci_hcd and address 8
[429522.506086] usb 2-1: configuration #1 chosen from 1 choice
[429522.510716] scsi14 : SCSI emulation for USB Mass Storage devices
[429522.511467] usb-storage: device found at 8
[429522.511469] usb-storage: waiting for device to settle before scanning
[429527.514559] usb-storage: device scan complete
[429527.518790] scsi 14:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[429527.519160] sd 14:0:0:0: Attached scsi generic sg3 type 0
[429527.543281] sd 14:0:0:0: [sdd] Attached SCSI removable disk

Any ideas on why this might be happening?

-Brant

---

### Post by sharkllama on 2010-07-21
Alright, 
   A slightly more informative dmesg output:

sharkllama@quaaludes:~/Scripts/BashScripts$ dmesg | tail
[439668.599317] EXT2-fs error (device sdc1): ext2_get_inode: unable to read inode block - inode=12476422, block=49905666
[439668.599430] EXT2-fs error (device sdc1): ext2_get_inode: unable to read inode block - inode=12476422, block=49905666
[439668.599543] EXT2-fs error (device sdc1): ext2_get_inode: unable to read inode block - inode=12484647, block=49938436
[439668.599659] EXT2-fs error (device sdc1): ext2_get_inode: unable to read inode block - inode=12484647, block=49938436
[439672.160147] usb 1-4: can't set config #1, error -110



-Brant

---

