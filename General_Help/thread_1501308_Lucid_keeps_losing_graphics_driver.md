---
title: "Lucid keeps losing graphics driver"
date: 2010-06-04
forum: General Help
---

### Post by JOZeldenrust on 2010-06-04
Hey everyone,

I'm having a weird problem with Lucid: whenever I boot my system, it seems to forget there's a graphics driver. The result is that windows don't have title bars, and anything involving fancy graphics is turned off.

When I go to the "appearance" settings, I can go to "visual effects", select "normal", and the machine starts looking for a driver, which is found. After that shading effects are once again on, but the windows still don't have title bars. If I then start the Compiz settings manager, that window and any window that appears thereafter does have a title bar.

That way my desktop configuration is pretty much how I want it. The problem is that after starting up again, all the wonkiness is back.

Any idea how I can fix this?

---

### Post by Bobulous on 2010-06-10
Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1503160](http://ubuntuforums.org/showthread.php?t=1503160)

I think this will work for you, as it works for someone else (reported in a thread in which you participate, in fact).

---

### Post by LowSky on 2010-06-10
press Alt+F2

Type ```
metacity --replace
```

---

