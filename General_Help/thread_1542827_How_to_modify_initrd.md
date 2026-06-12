---
title: "How to modify initrd?"
date: 2010-07-31
forum: General Help
---

### Post by schmadde on 2010-07-31
I need to modify the contents of the initrd image. Particularly, I want to exclude the usb_storage module from the initrd. In other distributions there is a config file that lists modules which should be included in initrd and initrd can be recreated with "mkinitrd". Is there a similar mechinism in ubuntu 10.04 and how do I use it? Modifying initrd by hand is out of the question because the change does not survive a kernel update.

Failing that: is there an equivalent to "boot.local" on other distributions, so I can rmmod usb_storage on boot?

Background is that I want to disable usb storage devices and blacklist.conf only helps if the storage devices are plugged in after boot.

thx
schmadde

---

