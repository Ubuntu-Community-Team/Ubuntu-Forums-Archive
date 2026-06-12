---
title: "KWin Effects lock up certain programs (11.04)"
date: 2011-05-08
forum: General Help
---

### Post by wd5gnr on 2011-05-08
Upgraded and been 99.9% happy. But...

I use the NVIDIA proprietary drivers. KWin has always worked fine for me in the past. I have a few Chrome application links I use. Now opening them in any way (including creating a new one and opening it) totally locks up X. Music is still playing and I can ssh in from elsewhere, so it isn't a crash/hang. But the display system is gone. Shutter (a screen capture app) does the same thing. It works until it takes the screen shot and tries to display it and then it hangs the same way. Xorg is up at 100%. Every other program I've run (Chrome itself, Dolphin, Emacs, Konsole, Konguerer, etc.) all work fine.

I can ssh in and kill X and Xorg and restart KDM and I get a corrupt login screen (well, only with the newest NVIDIA drivers; with the ones I had been running, it was corrupt).

Turning off effects lets it work fine? I have not tried each effect to see which one is causing the problem or if it is just compositing in general.

Anyone else have this problem?

UPDATE:
Well. 

1) Turned off effects. Chrome shortcuts worked.
2) Turned off all effects and renabled (left on logon/logoff effects). Chrome shortcuts worked.
3) Reenabled each effect one at a time. Worked each time.

So I can only conclude that something in .kde was not right and turning them all off and back on fixed it. I am going to try Shutter now but I suspect it will work ok. Yep. Shutter now works also. Hmm...

---

### Post by ranjan_mg on 2011-05-08
I am seeing this behavior as well. kopete locks up. and now I am seeing that when I use system settings to change window decorations, kwin locks up. I can ssh into the box, but I see that xorg is at 100%.
Using nvidia proprietary drivers.

---

### Post by wd5gnr on 2011-05-28
I am still having this trouble in different areas. If I try to "tear off" a tab in Chrome (that is, click on a tab and drag it to its own window) that is a 100% hang. If compositing is turned off it works. 

I suppose I should file a bug. Anyone else seeing this behavior?

---

### Post by wd5gnr on 2011-06-05
NVIDIA 275.09.04 (beta) fixes this.

---

