---
title: "Touchpad sensitivity way too high in fullscreen apps"
date: 2011-11-22
forum: General Help
---

### Post by raycluster on 2011-11-22
Hey folks ;)

I'm running **Ubuntu 11.10 32bits** on my **Acer 1810TZ**. It's touchpad is not working very well in some apps running in fullscreen mode. The speed of the mouse is way too high, the touchpad is extremely sensitive. It's basically not usable. This happens only in *some* programms (*Dungeons of Dreadmor*, *Gish*, *Frozen Synapse* or *Voxeltron* for example), and **only** in fullscreen mode. If I run it windowed everything is fine.
What's strange: USB-mices work just fine in both fullscreen and window mode. Whilst the touchpad is changing it's mode depending on the screen mode, the USB mouse is always configured correctly. The touchpad also changes it's sensitivity when the USB mouse is connected!

Could somebody help me with this problem? Of ourse I can use the USB mouse, but I do not always feel like taking it with me.

This might be a problem with the graphics engine of the games (altough I have not idea what engines are used, and google didnt help me either), because programs running on flash, or for example *Dungeon Crawl Stone Soup* (compiled by myself) work fine...

Greetings, Ray.

p.s.: The apps are always running on the screens native resolution, *1366x768*, just like the X-server

---

### Post by raycluster on 2011-11-22
I also encounter this problem now with crayon physics and aquaria :-( Help!

---

### Post by raycluster on 2011-11-23
Has nobody an idea?

---

### Post by spontex on 2011-11-27
Same here: playing Hedgewars on Lubuntu 11.10 with the touchpad of my eeePC 701 is impossble in fullscreen.

---

### Post by raycluster on 2011-11-29
Still no ideas?

---

### Post by spontex on 2011-11-29
I couldn't find a bug report on Launchpad. If none exists, we should file one.

---

### Post by louiedog on 2011-12-03
Same problem with ScummVM in lubuntu.

---

### Post by raycluster on 2011-12-11
Still looking for a solution. Has somebody reported the bug yet?

---

### Post by mr.frisky on 2012-09-12
Hi Ray,

I've nailed it - it's a problem (feature?) with SDL1.2, which many cross-platform games rely on.

The SDL library responds to several environment variables, one of which disables relative mouse positioning.

See if it works for you - open a console/terminal and:

```
export SDL_MOUSE_RELATIVE=0
```

then run your game from the console, for example:

```
hedgewars
```

Let me know if this works for you :)

Tim

---

### Post by Erol on 2012-12-31
This works. Thanks!

---

