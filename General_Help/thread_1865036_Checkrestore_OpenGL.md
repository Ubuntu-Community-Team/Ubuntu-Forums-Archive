---
title: "Check/restore OpenGL"
date: 2011-10-19
forum: General Help
---

### Post by ofnuts on 2011-10-19
In another thread I mention compositing problems in KDE. After digging a bit, it appears that compositing is OK with XRender, so I have to infer that my OpenGL is no longer working (however, Google Earth seems to work fine and as far as I know it uses OpenGL...). So how can I check the status of OpenGL and its configuration?

---

### Post by ajgreeny on 2011-10-19
> **ofnuts said:**
> In another thread I mention compositing problems in KDE. After digging a bit, it appears that compositing is OK with XRender, so I have to infer that my OpenGL is no longer working (however, Google Earth seems to work fine and as far as I know it uses OpenGL...). So how can I check the status of OpenGL and its configuration?
This is a problem of the two updates yesterday of **xserver-xorg-core** and **xserver-common**, which is known about and new packages are being compiled as I write this.  I am certain the new updates will be released very soon (tomorrow?).

You can either wait till then or you can force a downgrade to the older version using synaptic.  If you do that you must do it in the right order.
First highlight **xserver-xorg-core**, go to Package menu and choose "Force version" and you can choose the earlier version 2:1.7.6-2ubuntu7 instead of 2:1.7.6-2ubuntu7.8.

Now do the same for **xserver-common**, logout and in again and you will have full effects again.  Probably the new version without the GL problem will have been released by tomorrow, so you may be able to update again, but look for the version update from the 7.8 to the next, whatever that is.

---

### Post by ofnuts on 2011-10-19
> **ajgreeny said:**
> This is a problem of the two updates yesterday of **xserver-xorg-core** and **xserver-common**, which is known about and new packages are being compiled as I write this.  I am certain the new updates will be released very soon (tomorrow?).

You can either wait till then or you can force a downgrade to the older version using synaptic.  If you do that you must do it in the right order.
First highlight **xserver-xorg-core**, go to Package menu and choose "Force version" and you can choose the earlier version 2:1.7.6-2ubuntu7 instead of 2:1.7.6-2ubuntu7.8.

Now do the same for **xserver-common**, logout and in again and you will have full effects again.  Probably the new version without the GL problem will have been released by tomorrow, so you may be able to update again, but look for the version update from the 7.8 to the next, whatever that is.
OK, will wait for the update... didn't remember I had such an upgrade applied. Is there a way to list all recent updates?

Edit: I'm indeed on version  2:1.7.6-2ubuntu7.8... p, li { white-space: pre-wrap; } so I'll wait for the update and use Xrender in the meanwhile. Thx a lot.

Btw, is there a more reliable way to know when a package has been upgraded last than do perform and "ls -c" on the package components?

---

### Post by ofnuts on 2011-10-19
Just received the updates (as "security updates", ah!). They indeed fix everything. Thx

---

