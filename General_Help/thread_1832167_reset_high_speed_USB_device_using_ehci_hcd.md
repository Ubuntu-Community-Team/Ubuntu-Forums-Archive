---
title: "reset high speed USB device using ehci_hcd"
date: 2011-08-24
forum: General Help
---

### Post by Jamesss on 2011-08-24
Hi,

I know this is a common problem from the many posts on this forum and elsewhere on the internet but I haven't found a solution.

I'm using a Western Digital 2 TB external USB hard drive with a Dell Inspiron 2400 PC running Ubuntu 10.10 with the 2.6.35-30-generic kernel.

I am writing large mp3 files to the external drive which are being encoded in real time from the line in (with ecasound and lame), and about once every 10 times, the file fails to be recorded due to the error is dmesg | tail:

```
[83525.136028] usb 1-2: reset high speed USB device using ehci_hcd and address 2
```

I've tried changing /sys/block/sdb/device/max_sectors to all sorts of different sizes (64,128,256,1024) but this doesn't help.

I've tried ```
sudo mount -o remount,sync /dev/sdb1
``` but that didn't work either.

Is there a solution for this?

James

---

### Post by Jamesss on 2011-08-26
bump

---

### Post by Hizeh on 2011-12-08
I had the same issue with the same hard drive.  I never did figure out how to fix it so I changed hard drives.

I had the WD Elements 2TB External HD, USB2.0

---

