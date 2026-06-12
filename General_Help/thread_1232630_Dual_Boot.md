---
title: "Dual Boot"
date: 2009-08-05
forum: General Help
---

### Post by accooper on 2009-08-05
OK, I dual boot Ubuntu 9.04 and XP Pro.  But the boot screen has so many other entries I have to be quick and scroll down if I wish to boot to XP (which really is not a bad thing except my wife likes it).  How can I safely delete some of these entris with out messing things up?

Andrew

---

### Post by merlinus on 2009-08-05
```
gksudo gedit /boot/grub/menu.lst
```Look for this:

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

Change the timeout to 10.

The multiple entries are for older kernels.  Best to keep at least the next to the most recent, in case you run into problems with the current one.

---

