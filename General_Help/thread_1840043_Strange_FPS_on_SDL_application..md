---
title: "Strange FPS on SDL application."
date: 2011-09-06
forum: General Help
---

### Post by roadkillguy on 2011-09-06
I'm writing an SDL c++ application, but I can assure you my code isn't the issue.  Without recompiling, my app either has the problem or it doesn't.  It can be very temper-mental.

The problem is, when I wave the mouse around frantically, my app gets near 60FPS (Which is where v-sync puts it) and when I don't, it's very choppy and gets around 30FPS.  I know this isn't code-specific because when I comment out input handling altogether it does the exact same thing.  Again, sometimes it does this and other times it runs just fine.

It looks like this: (You can tell when I wave the mouse (Produce near constant input) and when I don't.)
```
FPS:0
FPS:31
FPS:35
FPS:32
FPS:54
FPS:59
FPS:58
FPS:61
FPS:60
FPS:59
FPS:60
FPS:42
FPS:45
FPS:33
FPS:34
FPS:28
FPS:42
FPS:41
FPS:48
FPS:47
FPS:39
FPS:36
FPS:44
FPS:32
FPS:28
FPS:31
FPS:27
FPS:39
FPS:37
FPS:56
FPS:59
FPS:58
FPS:58
FPS:59
FPS:61

```

I'm using gnome, but I doubt that has to do with it.

Thanks a bunch.

---

### Post by roadkillguy on 2011-09-07
Really not sure as to how constant input would speed up framerates other than it's got to be the window manager itself.

---

