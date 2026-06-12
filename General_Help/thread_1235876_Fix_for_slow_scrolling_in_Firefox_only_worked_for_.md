---
title: "Fix for slow scrolling in Firefox only worked for a day?"
date: 2009-08-09
forum: General Help
---

### Post by rainwalker on 2009-08-09
I tried adding 
```

	Option  "GlyphCache"	"1"
	Option  "InitialPixmapPlacement"	"2"

```
to the video device section of my xorg.conf as described in this thread: [http://ubuntuforums.org/showthread.php?t=1032131](http://ubuntuforums.org/showthread.php?t=1032131)

It worked yesterday when I did it and restarted X, but doesn't work today after shutting down and booting up this morning. The lines are still there, and I've tried killing X via Control+Alt+Backspace to give it a little kick and that did nothing.

Can anyone explain why that fix only worked until I rebooted, or at least explain what those two lines mean?
I have a 1 GB Nvidia Quadro FX 3700 running the 185.18.14 driver compiled myself according to the instructions at [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

