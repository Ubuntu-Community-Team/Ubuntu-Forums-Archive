---
title: "Powertop howto"
date: 2009-09-10
forum: General Help
---

### Post by raminaghrobis on 2009-09-10
Hi, I wanted to know how to get the changes you make via powertop permanent, because at the moment they cancel each time I close the application...

Thanks!

---

### Post by raminaghrobis on 2009-09-19
Bump

The two suggestions I get are:

Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequently for background VM activity

Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config

Anyone know how to make these permanent? And by the way what's "VM dirty writeback" supposed to mean, and what's "USB autosuspend" - does it mean it'll suspend when not used or just suspend?

---

### Post by Whiffle on 2009-09-19
It says its for the m1330, but its pretty universal.  Just test everything before you make it permanent.
[http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

---

### Post by raminaghrobis on 2009-09-22
Thanks, I'll try that out

---

