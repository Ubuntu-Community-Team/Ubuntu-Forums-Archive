---
title: "Can I start a full screen game in a window via the terminal?"
date: 2009-11-04
forum: General Help
---

### Post by Rytron on 2009-11-04
Hi.
Is there a way to start a full screen game in a window via the command line?
Also, does anyone know how to close a crashed/frozen game besides altgr + k + print screen sysrq?
Thank you.

---

### Post by Giblet5 on 2009-11-04
Sure. Open a terminal window, enter the command for the fullscreen game.

Example: ```
doom3
```

---

### Post by Rytron on 2009-11-04
Hi. No, I mean I want to start the game in a window rather than in full screen.

---

### Post by Giblet5 on 2009-11-04
> **Rytron said:**
> Hi. No, I mean I want to start the game in a window rather than in full screen.

That depends on whether it parses Xlib commandline options.

The best way to find out, and Napoleon will back me on this, is to try it:

```
somegamecmd -geometry 640x480
```

If not, try ```
somegamecmd --help
```

Some games will accept a "-windowed" option.

They'll all be different though.

---

### Post by Rytron on 2009-11-05
Cheers Giblet5.

):P

---

