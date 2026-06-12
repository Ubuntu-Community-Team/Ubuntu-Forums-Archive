---
title: "Audio down and computer won't shut down."
date: 2010-06-11
forum: General Help
---

### Post by ucal on 2010-06-11
I'm going to guess this has to do with me updating yesterday, as there were no problems before that.  Which kind of ticks me off, because I came back to ubuntu because I got tired of micromanaging updates in arch. 

Audio is down.  The volume can be changed, but it isn't reflected in the volume icon at the top of the screen.  Sound preferences show the only output available is a dummy speaker.  

When I try to restart or shut down, it just logs me out of my profile and takes me to the login screen.  

As always, if you need more info, just tell me where to find it.

---

### Post by X-Windows on 2010-06-11
Perhaps other users can help you with your sound problem, but to turn off your computer hold the power button for 7 seconds, if that fails you defiantly need to do a clean install.

---

### Post by ucal on 2010-06-11
> **X-Windows said:**
> Perhaps other users can help you with your sound problem, but to turn off your computer hold the power button for 7 seconds, if that fails you defiantly need to do a clean install.

No, that works, but I'd rather not resort to it.  I'd like to have the menu functionality restored.

---

### Post by ucal on 2010-06-11
Some more info.  Running Alsamixer, I'm able to change the volume settings for 3 devices, default, and 2 better sounding devices. But these devices don't show up in sound preferences, and I don't know how to select one device to be used over another in the terminal.

---

### Post by ucal on 2010-06-11
Solved it.  Turns out sudo poweroff showed my computer who's boss and now audio works, and I can turn it off through the menu.  >_>

---

### Post by m5ernel on 2010-06-17
I don't understand what to do exactly. Can you explain it please, for I have the same problem.

---

