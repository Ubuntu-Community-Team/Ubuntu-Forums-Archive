---
title: "external hdd i/o error"
date: 2011-04-15
forum: General Help
---

### Post by flyingsliverfin on 2011-04-15
Here's my strange problem:
I try to create/copy anything onto my external 500 gb hdd and it gives me
```
Error creating directory: Input/output error
```
Only Yesterday I copied on a movie and that worked fine. 
For some reason though, copying files off the hdd also works fine.

No errors in dmesg (I think):
```
[  174.803569] sd 5:0:0:0: [sdc] Write Protect is off
[  174.803577] sd 5:0:0:0: [sdc] Mode Sense: 2f 08 00 00
[  174.803582] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  174.809156] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  174.809165]  sdc: sdc1
[  174.879688] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  174.879697] sd 5:0:0:0: [sdc] Attached SCSI disk

```

/var/log/messages:
```
Apr 15 16:24:02 joshua-desktop kernel: [  169.668066] usb 1-8: new high speed USB device using ehci_hcd and address 5
Apr 15 16:24:02 joshua-desktop kernel: [  169.801104] usb 1-8: configuration #1 chosen from 1 choice
Apr 15 16:24:02 joshua-desktop kernel: [  169.801473] scsi5 : SCSI emulation for USB Mass Storage devices
Apr 15 16:24:07 joshua-desktop kernel: [  174.800658] scsi 5:0:0:0: Direct-Access     Seagate  Portable         0130 PQ: 0 ANSI: 4
Apr 15 16:24:07 joshua-desktop kernel: [  174.801388] sd 5:0:0:0: Attached scsi generic sg3 type 0
Apr 15 16:24:07 joshua-desktop kernel: [  174.802659] sd 5:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Apr 15 16:24:07 joshua-desktop kernel: [  174.803569] sd 5:0:0:0: [sdc] Write Protect is off
Apr 15 16:24:07 joshua-desktop kernel: [  174.809165]  sdc: sdc1
Apr 15 16:24:07 joshua-desktop kernel: [  174.879697] sd 5:0:0:0: [sdc] Attached SCSI disk

```

The only place that I get an error is when i manually mount it via bash:
```
Incomplete multi-sector transfer: magic: 0x58444e49  size: 4096  usa_ofs: 40  usa_count: 5  data: 54106  usn: 54105: Input/output error
Incomplete multi-sector transfer: magic: 0x58444e49  size: 4096  usa_ofs: 40  usa_count: 5  data: 54106  usn: 54105: Input/output error
Incomplete multi-sector transfer: magic: 0x58444e49  size: 4096  usa_ofs: 40  usa_count: 5  data: 54106  usn: 54105: Input/output error

```

Any ideas?

---

### Post by flyingsliverfin on 2011-04-15
I was just playing around and found something interesting.
When run ```
mkdir test
```, it gives me the Input/output error. However, if I then run 'ls' I get the error: 
```
ls: reading directory .: Input/output error
```
Even stranger is what happens afterward, when i run 'ls' again: it works, and the directory is there that I wanted to create.

---

### Post by flyingsliverfin on 2011-04-15
For some reason i found a fix under windows (NO!) anyway, here it is:

chkdsk E: /f

it fixed something about indexes I30 for file 5  and something about recovering orphaned files

Phew!

---

