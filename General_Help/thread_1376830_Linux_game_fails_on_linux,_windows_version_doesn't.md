---
title: "Linux game fails on linux, windows version doesn't fail with wine"
date: 2010-01-09
forum: General Help
---

### Post by Drojoke on 2010-01-09
Nevermind this topic. Just found out what i did wrong.

[B]Biggest fail ever: I installed AMD64 Xubuntu on a i386 machine. xD
[/B]

---

### Post by ThaddeusW on 2010-01-09
> 00:00.893: Server GLX vendor: SGI [1.2]
00:00.893: Client GLX vendor: SGI [1.4]

That is your problem right there. When you see SGI as your OpenGL vendor then you are running the SGI software renderer. Wine ignores the rendering driver type and runs the game using the very slow software driver.

Refer to this thread for the fix:
[http://ubuntuforums.org/showthread.php?t=1323714]("http://ubuntuforums.org/showthread.php?t=1323714")

---

