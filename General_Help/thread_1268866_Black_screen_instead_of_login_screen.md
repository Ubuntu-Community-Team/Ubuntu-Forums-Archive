---
title: "Black screen instead of login screen"
date: 2009-09-17
forum: General Help
---

### Post by Pyntix on 2009-09-17
I just installed Kubuntu 8.10, updated everything in Adept and then installed the nvidia driver 180. (with the automatic proprietary drivers installation program thing)

After following [this tutorial]("http://turbulentsky.com/ubuntu-904-screen-resolution-monitor-out-of-range-nvidia-driver-180.html") I added
```
Option “UseEdid” “False”
```
in the section Device in xorg.conf.

Now, everytime I start Kubuntu, the screen goes black and enters power saving mode just when the login screen should show itself (right after the usplashscreen). Nothing I press on the keyboard helps at all.

The same thing happened earlier today on the same computer with Kubuntu 8.04 and the 177 driver.

My graphics card is NVidia 7800 GT 256MB.

---

