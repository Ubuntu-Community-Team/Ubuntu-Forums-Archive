---
title: "Digial camera problems"
date: 2006-02-21
forum: General Help
---

### Post by mrhelpman on 2006-02-21
When I plug in my Kyocera finecam S5 camera into the USB port it does not mount properly.  It almost works in that I can see the camera when I look under the computer icon in nautilus.

However when I try and mount the volume. Either from Nautilus or by hand I get the following error message , twice.
> mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I look at dmesg I see there have been a number of errors when the camera was plugged in. Take a look at this lot (sorry for the rather long post):

Any ideas people?
> [4296769.595000] usb 4-2: new full speed USB device using ohci_hcd and address 3
[4296769.863000] SCSI subsystem initialized
[4296769.869000] Initializing USB Mass Storage driver...
[4296769.875000] scsi0 : SCSI emulation for USB Mass Storage devices
[4296769.877000] usb-storage: device found at 3
[4296769.877000] usb-storage: waiting for device to settle before scanning
[4296769.877000] usbcore: registered new driver usb-storage
[4296769.877000] USB Mass Storage support registered.
[4296774.877000]   Vendor: Kyocera   Model: Finecam S5        Rev: 0100
[4296774.877000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4296774.883000] usb-storage: device scan complete
[4296775.020000] SCSI device sda: 250880 512-byte hdwr sectors (128 MB)
[4296775.028000] sda: Write Protect is off
[4296775.028000] sda: Mode Sense: 0b 00 00 08
[4296775.028000] sda: assuming drive cache: write through
[4296775.054000] SCSI device sda: 250880 512-byte hdwr sectors (128 MB)
[4296775.062000] sda: Write Protect is off
[4296775.062000] sda: Mode Sense: 0b 00 00 08
[4296775.062000] sda: assuming drive cache: write through
[4296775.062000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4296775.107000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4296776.546000] SCSI error : <0 0 0 0> return code = 0x8000002
[4296776.546000] sda: Current: sense key: Medium Error
[4296776.546000]     Additional sense: Unrecovered read error
[4296776.546000] end_request: I/O error, dev sda, sector 250872
[4296776.546000] Buffer I/O error on device sda1, logical block 31355
[4296776.636000] SCSI error : <0 0 0 0> return code = 0x8000002
[4296776.636000] sda: Current: sense key: Medium Error
[4296776.636000]     Additional sense: Unrecovered read error
[4296776.636000] end_request: I/O error, dev sda, sector 250872
[4296776.636000] Buffer I/O error on device sda1, logical block 31355
[4296776.726000] SCSI error : <0 0 0 0> return code = 0x8000002
[4296776.726000] sda: Current: sense key: Medium Error
[4296776.726000]     Additional sense: Unrecovered read error
[4296776.726000] end_request: I/O error, dev sda, sector 250816
[4296776.726000] Buffer I/O error on device sda1, logical block 31348
[4296776.816000] SCSI error : <0 0 0 0> return code = 0x8000002
[4296776.816000] sda: Current: sense key: Medium Error
[4296776.816000]     Additional sense: Unrecovered read error
[4296776.816000] end_request: I/O error, dev sda, sector 250816
[4296776.816000] Buffer I/O error on device sda1, logical block 31348
[4296776.906000] SCSI error : <0 0 0 0> return code = 0x8000002
[4296776.906000] sda: Current: sense key: Medium Error
[4296776.906000]     Additional sense: Unrecovered read error
[4296776.906000] end_request: I/O error, dev sda, sector 250624
[4296776.906000] Buffer I/O error on device sda1, logical block 31324
[4296776.996000] SCSI error : <0 0 0 0> return code = 0x8000002
[4296776.996000] sda: Current: sense key: Medium Error
[4296776.996000]     Additional sense: Unrecovered read error
[4296776.996000] end_request: I/O error, dev sda, sector 250624
[4296776.996000] Buffer I/O error on device sda1, logical block 31324
[4296777.086000] SCSI error : <0 0 0 0> return code = 0x8000002
[4296777.086000] sda: Current: sense key: Medium Error
[4296777.086000]     Additional sense: Unrecovered read error
[4296777.086000] end_request: I/O error, dev sda, sector 250624
[4296777.086000] Buffer I/O error on device sda1, logical block 31324
[4296777.176000] SCSI error : <0 0 0 0> return code = 0x8000002
[4296777.176000] sda: Current: sense key: Medium Error
[4296777.176000]     Additional sense: Unrecovered read error
[4296777.176000] end_request: I/O error, dev sda, sector 250480
[4296777.176000] Buffer I/O error on device sda1, logical block 31306
[4296777.266000] SCSI error : <0 0 0 0> return code = 0x8000002
[4296777.266000] sda: Current: sense key: Medium Error
[4296777.266000]     Additional sense: Unrecovered read error
[4296777.266000] end_request: I/O error, dev sda, sector 250480
[4296777.266000] Buffer I/O error on device sda1, logical block 31306


---

