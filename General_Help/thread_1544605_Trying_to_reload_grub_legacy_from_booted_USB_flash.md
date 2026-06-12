---
title: "Trying to reload grub legacy from booted USB flashdrive of Ubuntu 9.04"
date: 2010-08-02
forum: General Help
---

### Post by oldtraveler on 2010-08-02
I wish to re-install grub legacy from my booted USB flash drive for Ubuntu 9.04.

Using the terminal for sudo grub I then go to >root (hd0,0) and then when I go to <setup (hd0) I get "Error 17: Cannot mount selected partition"

I have tried substituting /dev/sda in place of (hd0) but then I get "Error 11: Unrecognized device string"

What else can I try?

---

### Post by oldfred on 2010-08-02
On my machine whichever drive I boot is in grub hd0 and the USB is in BIOS the first hard drive if I have it plugged in to boot. Grub numbering seems to change depending on boot order, but on my system sda, sdb, & sdc never change. I think it only works when i boot thru another drive because of the search by UUID.

It may be hd1?

---

