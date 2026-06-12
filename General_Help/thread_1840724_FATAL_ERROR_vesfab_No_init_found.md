---
title: "FATAL ERROR vesfab No init found"
date: 2011-09-08
forum: General Help
---

### Post by Kaboontu on 2011-09-08
wont boot.

Fatal: Error inserting vesafb (lob/modules/2.6.38-11-generic/kernel/devices/videos/vesafb.ko) no such device.
No [init]("http://en.wikipedia.org/wiki/Init") found. Try passing init=bootang.

Can anyone help?
I am working against a deadline.
thnx.

++my hdd wont mount when I am on live
so that i can save my files cause i get

wrong fs type,bad option superblock on dev/sda5

---

### Post by TeoBigusGeekus on 2011-09-10
Seems like there are errors on your partition (or, unfortunately, the beginning of a hard disk failure).
If the partition is a linux one (ext2,3,4), boot up with a live cd/usb, fire up a terminal and give
```
sudo fsck /dev/sda5
```
to search for errors and hopefully correct them.

---

