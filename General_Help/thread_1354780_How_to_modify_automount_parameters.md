---
title: "How to modify automount parameters"
date: 2009-12-14
forum: General Help
---

### Post by moderaterain on 2009-12-14
Hi! I'm new here, so plese be gentle~:D

I'm working with ubuntu 9.10 and offen use usbdisk to transfer files.

It seems that my usbdisk is always mounted as "dmask=077,fmask=022", which is quite annoying, for I have to reassign privileges each time.

Is there any way to make it a "dmask=022, fmask=133" as default?

Looking forward to your reply!

---

### Post by kellemes on 2009-12-14
Does this help?
[http://solutionsandtips.blogspot.com/2009/05/uuid-fstab-and-automatically-mount-usb.html]("http://solutionsandtips.blogspot.com/2009/05/uuid-fstab-and-automatically-mount-usb.html")

---

### Post by moderaterain on 2009-12-14
> **kellemes said:**
> Does this help?
[http://solutionsandtips.blogspot.com/2009/05/uuid-fstab-and-automatically-mount-usb.html](http://solutionsandtips.blogspot.com/2009/05/uuid-fstab-and-automatically-mount-usb.html)

thx! It works somehow

Does it mean that I have to "make a note" for all my removable storage devices?

I remembered that there used to be some options which present in gconf-editor, but they seem to be no more existed...:(

---

