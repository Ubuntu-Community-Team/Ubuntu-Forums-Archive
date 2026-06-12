---
title: "video crash bug when turns off and on or changes resolution. Compaq CQ61"
date: 2011-07-14
forum: General Help
---

### Post by ninjaaron on 2011-07-14
So I have this laptop, and ever since updating to Ubuntu 11.04, the screen will freeze when it turns off to save power, especially if music or video are playing.  The screen picture will come up, and the mouse even moves, but I am unable to manipulate anything else on the screen.  Sometimes I can hit buttons in the active program, but I cannot see that they are hit.  However, when it's a music program or a video, I can hear the sound stop if I hit the pause button.  I cannot use the power button to turn it off at this point.  I am to do a forced hardware shutdown.

I recently downloaded the a for-pay game, Steel Storm: Burning Retribution, and it also seems to be affected by this bug when it tries to take over the screen. I have managed to close the program by intuition and following sounds, at which point the screen is restored to it's normal settings, but it is frozen and I have to do a forced shutdown.  I downloaded several other games to test this out, and many of them then resize the screen have the same problem, though some of them occasionally work and occasionally do not.  Of course, the only game that I actually paid for never works.

So, I don't like that.

---

### Post by ninjaaron on 2011-07-14
Neva' mind.  Google search for "11.04 screen freeze" and found a million pages with the fix.  In brief, get the package ccsm, open it, go to the OpenGL settings, and uncheck "Sync to VBlank."

That's all folks.

---

