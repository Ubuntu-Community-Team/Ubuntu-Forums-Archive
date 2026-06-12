---
title: "fat usb drive woun't mount"
date: 2006-05-17
forum: General Help
---

### Post by the_guy1 on 2006-05-17
My standerd 4 gig mini usb hard drive will not mount and it wont ditect that there is a drive there but the drive reconizes that it is there help me

---

### Post by Sutekh on 2006-05-17
Can you please input this command into a Terminal window (Appications -> Accessories Menu)
```
tail -f /var/log/messages
``` This should output some messages, and then wait for more input.  

Next plug in your USB hard drive and see what new messages appear. Hopefully it will tell you where it has assigned the USB drive, /dev/sda, /dev/sdb, etc.

Post them here if you like and we can work out where it is and how to mount it.

---

### Post by the_guy1 on 2006-05-18
> tail -f /var/log/messages
May 18 20:29:05 localhost kernel: [4297966.335000] SCSI device sda: 8388608 512-byte hdwr sectors (4295 MB)
May 18 20:29:05 localhost kernel: [4297966.336000] sda: Write Protect is off
May 18 20:29:05 localhost kernel: [4297966.339000] SCSI device sda: 8388608 512-byte hdwr sectors (4295 MB)
May 18 20:29:05 localhost kernel: [4297966.340000] sda: Write Protect is off
May 18 20:29:07 localhost kernel: [4297966.340000]  /dev/scsi/host4/bus0/target0/lun0: unknown partition table
May 18 20:29:07 localhost kernel: [4297968.606000] Attached scsi removable disk sda at scsi4, channel 0, id 0, lun 0
May 18 20:29:07 localhost scsi.agent[11253]:      sd_mod: loaded sucessfully (for disk)
May 18 20:31:35 localhost gconfd (root-10615): GConf server is not in use, shutting down.
May 18 20:31:35 localhost gconfd (root-10615): Exiting
May 18 20:32:06 localhost kernel: [4298147.808000] usb 5-8: USB disconnect, address 5
May 18 20:32:51 localhost kernel: [4298192.474000] usb 5-8: new high speed USB device using ehci_hcd and address 6
May 18 20:32:51 localhost kernel: [4298192.553000] scsi5 : SCSI emulation for USB Mass Storage devices
May 18 20:32:51 localhost usb.agent[12414]:      usb-storage: already loaded
May 18 20:32:56 localhost kernel: [4298197.581000]   Vendor: CREATIVE  Model: Zen Micro (UMS)   Rev: 0001
May 18 20:32:56 localhost kernel: [4298197.581000]   Type:   Direct-Access                 ANSI SCSI revision: 04
May 18 20:32:56 localhost kernel: [4298197.584000] SCSI device sda: 8388608 512-byte hdwr sectors (4295 MB)
May 18 20:32:56 localhost kernel: [4298197.585000] sda: Write Protect is off
May 18 20:32:56 localhost kernel: [4298197.588000] SCSI device sda: 8388608 512-byte hdwr sectors (4295 MB)
May 18 20:32:56 localhost kernel: [4298197.589000] sda: Write Protect is off
May 18 20:32:58 localhost kernel: [4298197.589000]  /dev/scsi/host5/bus0/target0/lun0: unknown partition table
May 18 20:32:58 localhost kernel: [4298199.749000] Attached scsi removable disk sda at scsi5, channel 0, id 0, lun 0
May 18 20:32:58 localhost scsi.agent[12466]:      sd_mod: loaded sucessfully (for disk) 

it still cant read/write it

---

