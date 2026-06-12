---
title: "ATI Driver rollback."
date: 2010-11-12
forum: General Help
---

### Post by Kcj1993 on 2010-11-12
I am affected by this bug [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/665734](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/665734) and I am wondering if (and how) I can rollback the drivers to the drivers supplied with 9.10.

Thanks.

---

### Post by Kcj1993 on 2010-11-15
Bump.

---

### Post by Cabalbl4 on 2010-11-15
You may use old ATI proprietary drivers:

[http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx)

Try one of these (I think it is about 9.7 somewhere). This should go. 

You may also try to install the latest driver. It works perfect by me.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=&lang=us&rev=10.10&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=&lang=us&rev=10.10&ostype=Linux%20x86)

---

### Post by Kcj1993 on 2010-11-15
The proprietary drivers don't support my hardware (Xpress 200M). I just want to know if and how I could install the open-source drivers that come with 9.10 since I didn't have any crashing issues with that driver.

---

### Post by Cabalbl4 on 2010-11-15
[http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/refs/tags](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/refs/tags)

here are the sources (xf86-video-ati)... You may try to build the older version, but i fear it will require a downgraded version of Xorg (and I do not know the way to downgrade it in new ubuntus (if there is one)).

[SIZE="1"]That's why I am still on 9.10: driver issues[/SIZE]

[http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building)

Here is the howto about radeon driver building... however, to work with karmic versions you need to revert sources list to karmic. And purge the package cache.

This is the hardest way, its results can not be predicted, I even would not try it myself. IMHO it is better to install karmic back. Or wait for the solution.

---

