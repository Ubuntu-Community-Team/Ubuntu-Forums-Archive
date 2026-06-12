---
title: "How may i mount an image file (created by dd) to make it appear as a usb drive"
date: 2009-07-09
forum: General Help
---

### Post by sefs on 2009-07-09
Hey all,

I created an image of a disk with dd.  I now want to mount it in ubuntu to make it appear as a external usb disk.

The reason I want to do this is so that I can use the mounted image in vmware by attaching it as a usb device.

Possible?

---

### Post by t4thfavor on 2009-07-10
Doesn't VMWare actually attach to the /dev/whatever. I don't think a mounted image could ever look like a usb device to vmware. You may be able to mount the actual image in vmware if you can transfer it over the shared drive or something.

---

