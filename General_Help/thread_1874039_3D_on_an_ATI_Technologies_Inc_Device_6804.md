---
title: "3D on an ATI Technologies Inc Device 6804?"
date: 2011-11-02
forum: General Help
---

### Post by hgernhardt on 2011-11-02
Folks—

I understand that the device mentioned in the subject line is inbuilt to the AMD processor which sits in my shiny new Compaq Presario CQ57.  The line from lspci is:

```
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9804
```The lines I see in Xorg.0.log are ( | grep \.so):
```

(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Unloading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so

```What I notice is that radeon_drv.so is being unloaded.  Is there something I am missing here?  I understand that this model doesn't work well out of the box with Lucid (fresh install).  Quite frankly, I want to get compiz running on this machine—I miss such features as expo and scale.  My question, then, is how do I get 3D working?  The device *should* work like something in the Radeon 6000 series.

I appreciate any and all help in this,

Henry

---

