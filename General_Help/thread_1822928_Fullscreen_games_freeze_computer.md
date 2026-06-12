---
title: "Fullscreen games freeze computer"
date: 2011-08-11
forum: General Help
---

### Post by u-noob-tu on 2011-08-11
every time i start up a game like armagetron advanced or blobby volley 2 in full screen it freezes my computer. ill launch the game, and when i do the screen goes black for a moment like its going to full screen but then shows a zoomed up view of the top left of desktop. and thats it, its frozen. i have to restart. does anyone have a clue why this happens?

---

### Post by u-noob-tu on 2011-08-12
*bump*

---

### Post by u-noob-tu on 2011-08-13
*BUMP* really? no one has had this issue before?

---

### Post by hakermania on 2011-08-13
No, I have (had) the same issue. Bumping only after 24 hours please.
**STEPS**
1) Install Compiz Config Settings Manager
2) Open it, search for opengl
3) click on opengl
4) Uncheck the Synk to VBlank
5) Restart
6) Retry

This works for most of the times, but sometimes it still stucks. For the latter, you can hit Ctrl+Alt+F1, type in your login name and passwd and give
```

sudo kill $(pidof X)

```This will bring you again to the login screen without hard-powering off the computer.
Note that when you give the above command you should then close the PC using (only for the current session, it's not permanent)
```

sudo shutdown -h now <-this for shutdown
sudo shutdown -r now <-this for restart

```because the usual shortcuts on the shutdown menu won't possibly work (they will result to the login screen as well)

---

### Post by u-noob-tu on 2011-08-13
yeah, it seemed to work the first time after changing vblank sync. second time i launched the game, though, it froze again.

---

### Post by hakermania on 2011-08-13
> **u-noob-tu said:**
> yeah, it seemed to work the first time after changing vblank sync. second time i launched the game, though, it froze again.
I haven't found a solution to this, it's a risk, but 
```

sudo kill $(pidof X)

```
is a quick way so as to avoid hard-restart and try again, so I use this anyway :/

---

