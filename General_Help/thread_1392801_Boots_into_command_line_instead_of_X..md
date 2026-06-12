---
title: "Boots into command line instead of X."
date: 2010-01-28
forum: General Help
---

### Post by iEthan on 2010-01-28
On my relatively new install, it's booting into command line instead of X--again.

This is the reason I reinstalled in the first place. This has happened to me three times now.

So, I boot up and it gets past GRUB, past the glowing Ubuntu option, then it prompts me for my username, then password. I run:

```
startx
```

And that starts the GUI for about a minute, then it runs the GUI login system.

To add to the mess, the network-applet is not shown in the panel. Additionally, Chrome will not launch (I ran Firefox from the terminal).

What's the problem here?

---

### Post by blueshiftoverwatch on 2010-01-28
I don't know what your problems are. But maybe you could bypass having to manually type in "startx" by making a startup script that would enter it in automatically. I've never done this (or had a reason to) personally, so I can't link you to any good articles. The most I've done is created scripts that launch after the GUI login screen to load/reload various things in the GUI that weren't initializing correctly. But a web search might yield some results.

---

