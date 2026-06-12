---
title: "One usb"
date: 2006-05-14
forum: General Help
---

### Post by kdevil on 2006-05-14
Argh, some error occurred when I posted this thread and the title got cut off, should be "One usb device shows up as two"

Originally, I had a USB flash drive that was working fine.  Then I tried partitioning it in gparted...

Originally it would show up as "488.7 MB Removable Volume".  Now when I put it in, two things appear: "488.7 MB Removable Volume" and "486.3 MB Removable Volume".

However, if I start up Knoppix (kernel 2.6.12), it shows up as just one.

Any idea how I can get it back to showing up as just one volume again?

---

### Post by kdevil on 2006-05-15
Fixed it.

For anyone else who runs into this problem:  First get anything you want to save off of the drive (although this should go without saying), then give it a round of /dev/zero (dd if=/dev/zero of=/dev/sda, which I then ctrl-c'd it after maybe 7 seconds).  Then, make sure there's nothing from the flash drive mounted in /media (actually, maybe I should've done this before the zeroing...).  After that, you can just go into gparted and format it like normal.

---

