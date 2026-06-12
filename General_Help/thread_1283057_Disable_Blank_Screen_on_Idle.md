---
title: "Disable Blank Screen on Idle"
date: 2009-10-05
forum: General Help
---

### Post by xnevermore on 2009-10-05
I'm currently using Openbox and I don't have any screensavers running. I also have all of the put to sleep options in the Power Management Preferences set to Never.

Despite this, my screen keeps going blank (monitor turns off) after about five minutes of being idle (not moving the mouse or typing on the keyboard). I looked into the possibility that it might be a BIOS setting that's causing this, but that's not the case.

What is causing this behavior and how do I stop it?

---

### Post by xnevermore on 2009-10-10
Bump? Anyone?

---

### Post by TheNerdAL on 2009-10-10
There is hardly any help here. Ughh.

---

### Post by mechro on 2009-10-10
Solution might be here...

[http://crunchbanglinux.org/forums/topic/229/disable-screensaver/](http://crunchbanglinux.org/forums/topic/229/disable-screensaver/)

Although it refers to screensaver, I think it's the same issue as yours.

Good Luck.

---

### Post by xnevermore on 2009-10-20
Ok. So I've found a solution. First, you can find some background information [here]("http://www.shallowsky.com/linux/x-screen-blanking.html"). Apparently, this screen blanking behavior is built into Xorg.

I've figured out how to turn it off using these commands:

```
xset s off
xset -dpms
xset s noblank
```

---

### Post by StuartN on 2009-10-20
> **xnevermore said:**
> Apparently, this screen blanking behavior is built into Xorg.

It would be nice if, when you install a new screen-saver in the upper, desktop layer of Gnome, that it would automatically disable the screen-saver in the lower xorg layer. Overall though, there are few problems of this kind of layer conflict.

---

### Post by xnevermore on 2009-10-20
Yeah, I don't know. Maybe it does. I don't have a screensaver installed for Openbox, so I don't know if installing one disables it.

---

### Post by StuartN on 2009-10-20
> **xnevermore said:**
> I don't have a screensaver installed for Openbox, so I don't know if installing one disables it.

I don't know Openbox, but the Gnome screensaver and power management processes are always running their countdown, whether or not you have enabled a screensaver or power scheme. I manage most window managers also install and start a countdown process.

---

