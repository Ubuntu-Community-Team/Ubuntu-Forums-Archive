---
title: "USB ports playing up?"
date: 2012-05-28
forum: General Help
---

### Post by todaymueller on 2012-05-28
I first noticed my external hard drive was not uploading files. I have now found that photos and video from cameras will also not download through any of the USB ports. Fortunately the wireless keyboard and mouse are still functioning. Anyone got any ideas on what may be occurring? 
I am using Lucid Lynx on one hard drive and Hardy Heron on another the problem is the same on both. I have tried different leads and different ports ie both at the front and back of the PC, but no joy :(

---

### Post by matt_symes on 2012-05-28
Hi
 
Unplug the device, open a terminal and type
 
```
 
tail /var/log/syslog

```
 
Plug the device back in to get the log. Post it back here if you want as that may gicve clues.
 
Kind regards

---

### Post by todaymueller on 2012-05-28
john@john-desktop:~$ tail /var/log/syslog
May 28 17:38:54 john-desktop kernel: [  411.692283] sd 4:0:0:0: [sdc] Mode Sense: 18 00 00 08
May 28 17:38:54 john-desktop kernel: [  411.692286] sd 4:0:0:0: [sdc] Assuming drive cache: write through
May 28 17:38:54 john-desktop kernel: [  411.695152] sd 4:0:0:0: [sdc] Assuming drive cache: write through
May 28 17:38:54 john-desktop kernel: [  411.695158]  sdc: sdc1
May 28 17:38:54 john-desktop kernel: [  411.699158] sd 4:0:0:0: [sdc] Assuming drive cache: write through
May 28 17:38:54 john-desktop kernel: [  411.699168] sd 4:0:0:0: [sdc] Attached SCSI removable disk
May 28 17:38:55 john-desktop kernel: [  411.956427] FAT: Invalid FSINFO signature: 0x00000000, 0x00000000 (sector = 1)
May 28 17:39:13 john-desktop AptDaemon: INFO: Quiting due to inactivity
May 28 17:39:13 john-desktop AptDaemon: INFO: Shutdown was requested
May 28 17:39:47 john-desktop kernel: [  463.988769] FAT: Invalid FSINFO signature: 0x00000000, 0x00000000 (sector = 1)
john@john-desktop:~$ 

Well blow me down I managed to download some video files off my camera.
Not sure if any of the above helps or whether the problem has gone away?

---

### Post by matt_symes on 2012-05-28
Hi
 
>  
May 28 17:38:55 john-desktop kernel: [ 411.956427] FAT: Invalid FSINFO signature: 0x00000000, 0x00000000 (sector = 1)


 
I'm not sure if that is a problem or not. It's not an error i have conme accross before.
 
It does seem to be seeing the USB devices though. What devices have not been working ? Try one of them and post a new log back.
 
Kind regards

---

### Post by todaymueller on 2012-05-28
Nope, just tried my external hard drive and it slows everything down to a crawl, mouse pointer is sluggish and things are just not working. When I switch off the external HD things back up and running.

---

### Post by matt_symes on 2012-05-28
Hi
 
That's odd. 
 
Try running fsck in the external drive if it's extX or chkdsk if NTFS. Run a SMART terst in the drive as well.
 
Is there anything else in the logs ?
 
Kind regards

---

### Post by todaymueller on 2012-05-28
john@john-desktop:~$ tail /var/log/syslog
May 28 18:00:02 john-desktop kernel: [ 1679.372794] scsi 6:0:0:0: Direct-Access     Seagate  Desktop          0130 PQ: 0 ANSI: 4
May 28 18:00:02 john-desktop kernel: [ 1679.374832] sd 6:0:0:0: Attached scsi generic sg3 type 0
May 28 18:00:02 john-desktop kernel: [ 1679.382764] sd 6:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
May 28 18:00:02 john-desktop kernel: [ 1679.383343] sd 6:0:0:0: [sdc] Write Protect is off
May 28 18:00:02 john-desktop kernel: [ 1679.383347] sd 6:0:0:0: [sdc] Mode Sense: 2f 08 00 00
May 28 18:00:02 john-desktop kernel: [ 1679.383351] sd 6:0:0:0: [sdc] Assuming drive cache: write through
May 28 18:00:02 john-desktop kernel: [ 1679.385112] sd 6:0:0:0: [sdc] Assuming drive cache: write through
May 28 18:00:02 john-desktop kernel: [ 1679.385118]  sdc: sdc1
May 28 18:00:02 john-desktop kernel: [ 1679.408845] sd 6:0:0:0: [sdc] Assuming drive cache: write through
May 28 18:00:02 john-desktop kernel: [ 1679.408854] sd 6:0:0:0: [sdc] Attached SCSI disk
john@john-desktop:~$ 

Everything slows to a crawl when I switch on the external HD.

---

### Post by matt_symes on 2012-05-28
Hi
 
It's recognising and connecting the drive. 
 
Check all the cables and try a different one if possible. 
 
It's plugged into the correct port ? Like i said, run a smart test and fsck or chkdsk on the drive
 
Kind regards

---

### Post by todaymueller on 2012-05-28
Thanks for the help. I will have a bash tomorrow. Got to go to work now. :mad:

---

