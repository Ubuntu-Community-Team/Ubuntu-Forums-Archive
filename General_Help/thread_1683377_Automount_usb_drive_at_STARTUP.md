---
title: "Automount usb drive at STARTUP"
date: 2011-02-07
forum: General Help
---

### Post by ledom on 2011-02-07
Hi,

I am trying to use my lod EEEpc 701 as file server.
I use s3g (sg_start) to spindown my drives (usb drives), but it seems to need mounted drives to work.
What is the best way to automount already plugged drives at startup (not when plug it) with xfce?
Thanks

---

### Post by Brandon Williams on 2011-02-07
On a similar setup with a Dell Mini-9, my USB drives are recognized at boot-time, so I just added them to /etc/fstab. They are auto-mounted just fine.

---

### Post by ledom on 2011-02-08
Thanks Brandon, My disks are recognize too but not mounted, I also need to mount them via fstab.
But what I need is mounting all disks whitout configuring fstab.

---

