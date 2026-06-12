---
title: "Unity, GNOME Shell, and KDE side-by-side?"
date: 2011-10-22
forum: General Help
---

### Post by liquid150 on 2011-10-22
I installed both Gnome Shell and the KDE desktop, expecting to be able to choose between Unity and the other two at login.

The login screen defaults to KDE, and for some reason I can only access Gnome SHELL...well, there are other options like Ubuntu but Unity does not actually show up. I can't acccess any of my apps from the weird desktop that is not unity but also not Shell or KDE...

What's going on? Any way to fix this?

---

### Post by crdlb on 2011-10-22
It sounds like kdm was installed and you let it be set as the default display manager. You can restore lightdm with ```
sudo dpkg-reconfigure lightdm
```

If I misunderstood and you're still using lightdm, I don't know what's wrong. There shouldn't be any reason why you can't have them all installed.

---

### Post by deserthowler on 2011-10-22
> **liquid150 said:**
> I installed both Gnome Shell and the KDE desktop, expecting to be able to choose between Unity and the other two at login.

The login screen defaults to KDE, and for some reason I can only access Gnome SHELL...well, there are other options like Ubuntu but Unity does not actually show up. I can't acccess any of my apps from the weird desktop that is not unity but also not Shell or KDE...

What's going on? Any way to fix this?

Ubuntu is Unity on my install of 11.10.

Earl

---

### Post by liquid150 on 2011-10-22
crdlb was right. I switched over to lightdm and my problem was fixed.

Looks like the Ubuntu kdm isn't set up to handle all the options available to me. I don't know what crazy desktop was loading when I chose ubuntu from kdm, but it wasn't unity.

---

