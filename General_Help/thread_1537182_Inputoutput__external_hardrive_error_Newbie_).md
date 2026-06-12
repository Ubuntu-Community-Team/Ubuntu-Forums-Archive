---
title: "Input/output  external hardrive error **Newbie :) **"
date: 2010-07-23
forum: General Help
---

### Post by TomLum on 2010-07-23
Hi guys im new to linux and need some help with a problem. I installed Ubuntu 10.04 two days ago and was using my 1tb passport external HDD with it to download and store files. 
However today whenever i try and copy/cut and past to the HDD i get this error message..

Error opening file '/media/My Passport/test.avi': Input/output error

This is obviously very fustrating and i want to stay with Linux but i do need to fix this problem else im afraid im going to have to back to awful windows. Thankyou for any help guys :)

Tom

---

### Post by mdramige on 2010-07-23
This might be too basic, but have you tried unplugging the USB cable and then replugging it to force Gnome to remount the drive? If so, listing what you've tried already would be helpful.

---

### Post by TomLum on 2010-07-23
Hi thanks for reply. I have tried this yes. I unmounted, removed usb then plugged back in and it reads everything fine but still comes up with errors when copy/cutting.  I have also tried restarting computer.

---

### Post by nemilar on 2010-07-23
If you perform the action to cause the error, and then you do:

```
dmesg
```

do you see any useful information towards the end of the output?

---

### Post by TomLum on 2010-07-23
Hi yes i got this output near the end..

[19743.390354] sr1: scsi3-mmc drive: 51x/51x caddy
[19743.390496] sr 4:0:0:1: Attached scsi CD-ROM sr1
[19743.390692] sr 4:0:0:1: Attached scsi generic sg3 type 5
[19743.390786] ses 4:0:0:2: Attached Enclosure device
[19743.390841] ses 4:0:0:2: Attached scsi generic sg4 type 13
[19743.392851] sd 4:0:0:0: [sdb] Write Protect is off
[19743.392855] sd 4:0:0:0: [sdb] Mode Sense: 23 00 10 00
[19743.392859] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[19743.395761] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[19743.395767]  sdb: sdb1
[19743.434601] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[19743.434607] sd 4:0:0:0: [sdb] Attached SCSI disk
[19744.060616] UDF-fs: Partition marked readonly; forcing readonly mount
[19744.061392] UDF-fs INFO UDF: Mounting volume 'WD SmartWare', timestamp 2009/11/14 01:34 (103c)

does this make any sense to you? Thank you for your time and help.

Tom

---

