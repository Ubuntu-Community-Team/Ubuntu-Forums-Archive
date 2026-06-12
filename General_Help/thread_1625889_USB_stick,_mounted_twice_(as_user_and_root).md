---
title: "USB stick, mounted twice (as user and root)"
date: 2010-11-19
forum: General Help
---

### Post by idovecer on 2010-11-19
When I put my USB stick it is mounted automatically as /media/usb0 with root privileges.

In GUI in Places there are two:
1. USB 1GB (with user rights, but can't open it while usb-0 is mounted)
2. usb-0 (with root rights)

If I choose USB 1GB I can't access it. 
If I use usb-0 it opens in nautilus but can create, copy, remove anything because it has root rights (permissions).

If I umounted in shell with::
umount /media/usb0
In Places then is only USB 1GB, and it works normally as it should.

My question is:
How to remove automounting USB stick as usb-0 in /media/usb-0 with root privileges?

Thank you.

---

