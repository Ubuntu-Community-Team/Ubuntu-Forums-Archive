---
title: "finding graphics driver"
date: 2010-07-15
forum: General Help
---

### Post by sundays211 on 2010-07-15
as my graphics driver has been giving me a lot of trouble lately I would like to know how to find out which driver I am using. can anyone tell me how I can find this out?

---

### Post by anglican on 2010-07-15
> **sundays211 said:**
> as my graphics driver has been giving me a lot of trouble lately I would like to know how to find out which driver I am using. can anyone tell me how I can find this out?
I'm not sure of a guaranteed way to do this, I would look in /var/log/Xorg.0.log for this, perhaps something like:

```
grep /usr/lib/xorg/modules/drivers /var/log/Xorg.0.log
```is the simplest one-liner I could think of.

H

---

### Post by sundays211 on 2010-07-15
doing this it has come up with three drivers. how can I tell which one is the active one?

```

(II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so

```

---

### Post by anglican on 2010-07-16
> **sundays211 said:**
> doing this it has come up with three drivers. how can I tell which one is the active one?

```

(II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so

```
Well, it's loaded vesa and fbdev... and then unloaded them, so only openchrome remains. Openchrome is:
> A free and Open Source video driver for the VIA/S3G UniChrome, UniChrome Pro and Chrome9 graphics chipsets.(CLE266, KM400/KN400/KM400A/P4M800, CN400/PM800/PN800/PM880, K8M800, CN700/VM800/P4M800Pro, CX700, P4M890, K8M890, P4M900/VN896/CN896, VX800, VX855)



H

---

### Post by sundays211 on 2010-07-18
ahh, thanks

---

