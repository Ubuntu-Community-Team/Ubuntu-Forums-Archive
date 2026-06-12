---
title: "[mi] miSpriteRealizeCursor called for floating device. ?"
date: 2010-08-22
forum: General Help
---

### Post by dek8 on 2010-08-22
i had a guy tell me how to get a xorg config log.. and i have alot of this **"[mi] miSpriteRealizeCursor called for floating device."** in the log.. what is it? im very new to linux, i tried googling it, it comes up with easystroke which im using... any way to fix it?

---

### Post by estragib on 2010-08-23
I have the same.

As I understand, easystroke changed its way of handling the mouse cursor. Ubuntu bug [log spam when detaching a slave device]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/566375") and xorg/xserver commit [mi: remove log-spamming bogus error message (#26843)]("http://cgit.freedesktop.org/xorg/xserver/commit/?id=241b53b77750b5eea6759e79b23be4ff270a3d1f") seem to suggest this is nothing to worry about, just a library still warning about something that's no problem really, and fixed in xserver 1.8 anyway.

To find out if you're still on an 1.7.* xserver, you could do a ```
dpkg-query -l xserver-common xserver-xorg-core
``` which, for me, yields this output:

```
ii  xserver-common               2:**1.7.6**-2ubuntu7.3           common files used by various X servers
ii  xserver-xorg-core            2:**1.7.6**-2ubuntu7.3           Xorg X server - core server
```

If so, this will probably solve itself with future updates.

---

### Post by dek8 on 2010-08-28
do we update xorg or?

im on 1.7.6

---

