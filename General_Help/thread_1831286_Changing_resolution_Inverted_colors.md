---
title: "Changing resolution? Inverted colors?"
date: 2011-08-23
forum: General Help
---

### Post by TheFreakyChakra on 2011-08-23
Hey everyone! Newbie Ubuntu user here :D really liking it so far, besides the obvious linux issues (incompatibility)

I recently repaired a monitor and it asks me to change my resolution to 1140 x 900, the colors on the screen are inverted as well (for some weird *** reason)
I went into the Ubuntu settings and, well, they suck. Highest resolution I can choose is 1024X768, it then jumps straight to 960x540 -- 54 hertz is also the highest setting, I need to switch that to 60. Could someone explain how I can 
1.invert the colors so they show up NORMAL on my  other monitor
2.Tell me how to change the resolution to 1140 x 900
3.Tell me how to change the hertz

Thanks!!!!!!!!!!!
-Taylor

---

### Post by realzippy on 2011-08-23
What do you mean exactly by inverted colors?
May be you connected something wrong during repair?

Which graphics card,monitor,ubuntu version?

For help with resolution show output from:

```
xrandr -q
```

Although if you cannot fix the color fixing resolution might be useless..

---

### Post by realzippy on 2011-08-23
If you mean "negative" with inverted,you could test:

```
sudo apt-get install xcalib
```

```
xcalib -invert -alter
```

---

### Post by CatKiller on 2011-08-23
> **TheFreakyChakra said:**
> 54 hertz is also the highest setting, I need to switch that to 60.

No you don't. It's not actually 54 Hz.

The NVidia tool will show you the actual refresh rate since it's NVidia's driver that lies about the refresh rate to all the other tools.

---

