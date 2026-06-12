---
title: "reset display settings"
date: 2012-05-02
forum: General Help
---

### Post by goltoof on 2012-05-02
I can't get desktop effects to work. They were working before, now after some update they aren't working.  I'm using the default display drivers in 12.04.  I'm not using nVidia, can't use nVidia.

What do I got to do to get desktop effects to work??

I've tried every combination of settings in compiz... I just want to reinstall everything that'll take everything display related back to a fresh install state.  But what?

---

### Post by grahammechanical on 2012-05-02
You will not be able to get desktop effects to work if you are in Ubuntu 2D mode.

You may need to install a proprietary driver (Nvidia) in order to use Ubuntu (3D) mode which is what you need to use for desktop effects.

Ubuntu (Unity 3D) uses Compiz compositing or window manager. And we get 3D effects with Compiz.

Ubuntu 2D is the fall back mode for systems that cannot run 3D. It uses Metacity as the compositing or window manager. We do not get 3D effects with Metacity.

Regards.

---

### Post by goltoof on 2012-05-02
> **grahammechanical said:**
> You will not be able to get desktop effects to work if you are in Ubuntu 2D mode.

You may need to install a proprietary driver (Nvidia) in order to use Ubuntu (3D) mode which is what you need to use for desktop effects.

Ubuntu (Unity 3D) uses Compiz compositing or window manager. And we get 3D effects with Compiz.

Ubuntu 2D is the fall back mode for systems that cannot run 3D. It uses Metacity as the compositing or window manager. We do not get 3D effects with Metacity.

Regards.


Thanks, I'll read up on it, but is there anything I can check to see which one I'm running, what I need to uninstall/reinstall to get my old desktop back?

As I stated it was working before, until I did some upgrade and tried setting up multiple monitors.  I know I'm more than capable of running 3D, but something somewhere along the way apparently made it think otherwise.

---

### Post by goltoof on 2012-05-02
```

echo $DESKTOP_SESSION

```

Shows I was in 2d fallback.

This solved it for me:
```

apt-get purge xserver-xorg
apt-get install xserver-xorg xserver-xorg-video-all
reboot

```

---

