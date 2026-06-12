---
title: "Long blank screen delay after GRUB when booting Lucid, 5-10 minutes!"
date: 2010-09-18
forum: General Help
---

### Post by Giggity on 2010-09-18
This has been a problem for me for over a month, but only with Lucid.  I start the computer, or reboot it after a kernel upgrade.  After the GRUB selection, there is a blank screen and zero hard drive activity for something like 5-10 minutes.  Then the boot process proceeds as normal and everything is fine until the next time I reboot.

My computer is almost always being used for something, even when I'm asleep, so I'd like to avoid having to just wait until I go to bed to update and reboot.  I've searched, and all of the posts I've found involve not booting at all, which isn't the problem here.

I've attached my /var/log/boot.log, which I can't comprehend.  Of particular curiosity are the lines including:

```
udevd[365]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device...
```I've also included a hardware listing in case there is a compatibility issue with my aging hardware.  It's tarballed and gzipped since the only output method I could find was HTML, which is not a legal attachment here.

Thanks in advance to anyone who can help!

---

### Post by blueridgedog on 2010-09-18
Is the behavior the same with other kernel boot options?  Is it the same booting from a live CD?  Do you have more than one hard disk?

---

### Post by kerry_s on 2010-09-18
is it a toshiba? if so search the forum, there is a fix.

---

