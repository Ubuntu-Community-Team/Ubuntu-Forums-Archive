---
title: "Media such as SD Cards or Thumb Drives do not automount althought everything is fine"
date: 2009-12-25
forum: General Help
---

### Post by ManDay on 2009-12-25
Hi guys,

usually my devices should automount as soon as I plug them in, but they don't. The gconf-setting for media-automount is enabled, and dmesg has nothing besides the ordinary:

---
[73840.461173] usb 1-5: new high speed USB device using ehci_hcd and address 9
[73840.594155] usb 1-5: configuration #1 chosen from 1 choice
[73840.597634] scsi7 : SCSI emulation for USB Mass Storage devices
[73840.598696] usb-storage: device found at 9
[73840.598710] usb-storage: waiting for device to settle before scanning
[73845.596386] usb-storage: device scan complete
[73845.597202] scsi 7:0:0:0: Direct-Access     Single   Flash Reader     1.00 PQ: 0 ANSI: 0
[73845.599392] sd 7:0:0:0: Attached scsi generic sg1 type 0
[73846.251179] sd 7:0:0:0: [sdb] 3935232 512-byte logical blocks: (2.01 GB/1.87 GiB)
[73846.252020] sd 7:0:0:0: [sdb] Write Protect is off
[73846.252040] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[73846.252056] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[73846.259272] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[73846.259296]  sdb: sdb1
[73846.271376] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[73846.271406] sd 7:0:0:0: [sdb] Attached SCSI removable disk
---

The medium itsself is in the same working state as it was when it worked the last time (before I installed karmic from scratch).

---

### Post by L_V on 2009-12-27
Try to add the bold line to this file: /usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi (line 179)

>       <!-- allow these mount options for vfat -->
      <match key="volume.fstype" string="vfat">
	<match key="/org/freedesktop/Hal/devices/computer:system.kernel.name" string="Linux">
**	  <append key="volume.mount.valid_options" type="strlist">flush</append>**
	  <append key="volume.mount.valid_options" type="strlist">utf8</append>

and reboot.

---

### Post by Gibby13 on 2010-01-29
Worked for me!! Thanks I already had that line in the file but it was about 4 or 5 lines done, just added the extra line and rebooted.

Ubuntu 9.10 64bit.

---

