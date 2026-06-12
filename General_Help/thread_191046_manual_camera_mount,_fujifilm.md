---
title: "manual camera mount, fujifilm?"
date: 2006-06-07
forum: General Help
---

### Post by jms830 on 2006-06-07
I am trying to get my Fujifilm finepix a345 working. gphoto2 doesn't detect it. I've been trying to manually mount it, but I can't figure out where it is in /dev/ 

When I use the command "dmesg" I get this output toward the end:


```
[4433273.738000]   Vendor: FUJIFILM  Model: USB Mass Storage  Rev: 1.00
[4433273.738000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4433273.744000] SCSI device sdb: 512000 512-byte hdwr sectors (262 MB)
[4433273.748000] sdb: Write Protect is off
[4433273.748000] sdb: Mode Sense: 18 00 00 08
[4433273.748000] sdb: assuming drive cache: write through
[4433273.757000] SCSI device sdb: 512000 512-byte hdwr sectors (262 MB)
[4433273.761000] sdb: Write Protect is off
[4433273.761000] sdb: Mode Sense: 18 00 00 08
[4433273.761000] sdb: assuming drive cache: write through
[4433273.761000]  /dev/scsi/host17/bus0/target0/lun0: p1
[4433273.777000] Attached scsi removable disk sdb at scsi17, channel 0, id 0, lun 0
[4433273.779000] usb-storage: device scan complete
[4433346.455000] usb 2-2: USB disconnect, address 19
[4433497.371000] usb 2-2: new full speed USB device using uhci_hcd and address 20
[4433497.463000] scsi18 : SCSI emulation for USB Mass Storage devices
[4433497.465000] usb-storage: device found at 20
[4433497.465000] usb-storage: waiting for device to settle before scanning
[4433502.468000]   Vendor: FUJIFILM  Model: USB Mass Storage  Rev: 1.00
[4433502.468000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4433502.486000] Attached scsi removable disk sdb at scsi18, channel 0, id 0, lun 0
[4433502.489000] usb-storage: device scan complete

```

---

### Post by Sutekh on 2006-06-07
[quote=jms830]
Attached scsi removable disk **sdb** at scsi18, channel 0, id 0, lun 0[/quote] 
It looks like it has been given the device node /dev/sdb.

Are any partitions listed with
```
sudo fdisk -l
```

---

### Post by jms830 on 2006-06-07
that command lists:

```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         973     7815591    7  HPFS/NTFS
/dev/hda2             974        1946     7815622+  83  Linux
/dev/hda3            1947       14468   100582965    b  W95 FAT32
/dev/hda4           14469       14593     1004062+  82  Linux swap / Solaris

Disk /dev/hdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       48641   390708801    7  HPFS/NTFS

```

---

