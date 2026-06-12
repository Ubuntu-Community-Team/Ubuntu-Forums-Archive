---
title: "Ctrl+Alt+Backspace doesn't work, then what?"
date: 2011-07-06
forum: General Help
---

### Post by tomkat3 on 2011-07-06
Hey everybody,

I'm running Ubuntu 10.04 on a Dell d630 with an nVidia Quadro NVS 135M. My work requires me to run some intense programs running OpenGL, which sometimes creates problems.

So my computers had tons of graphics problems lately (probably nVidia's fault, just say'in :roll:). My attempts to fix these issues have muddled things up so bad that think I'll just reinstall the OS when my internship ends, but this isn't what I'm worried about now.

What tends to happen is this: the screen sometimes (the random nature makes it more frustrating](*,)) starts flickering when I start an innocent youtube video, or it might simply freeze when I run one of the intense programs mentioned above. 

Basically, what's bugging me is this: one program screws up bad enough, and takes everything else with it. Pressing Ctrl+Alt + Backspace or F2 has no effect. I have the force quit app on my taskbar, but I can't use it because its frozen! I always end up holding down the power switch to force shutdown my whole computer.

What is happening in these cases that Ubuntu doesn't respond to the keyboard commands?
Is there another key combination I could try that's easier on my computer than force powering off?

---

### Post by coffeecat on 2011-07-06
Ctrl-Alt-Backspace simply killed the xserver and took you back to the login screen. It was disabled by default in the gnome version that came with Lucid, if memory serves me correct. To re-enable it, go to System > Preferences > Keyboard. Then Layouts tab > Options > Key sequence to kill xserver and tick the ctrl-alt-Backspace box. I'm going from memory here prompted by what's available in the Natty desktop, so there might be minor details different in Lucid, but you can re-enable that key combination in Keyboard preferences.

However if the desktop freezes, ctrl-alt-Backspace may not work even if re-enabled. Then you have to use magic key combinations:

[http://en.wikipedia.org/wiki/Magic_keys](http://en.wikipedia.org/wiki/Magic_keys)

Use Alt + PrtScreen/SysReq + whichever letter key. On some keyboards/systems you need to use the AltGr key. Try Alt+PrintScr+K to kill the xserver, or if things are really bad, Alt+Print and R-E-I-S-U-B (slowly, one after the other) to reboot gracefully.

---

### Post by CatKiller on 2011-07-06
coffeecat's already told you about re-enabling the zap combination. Another, less drastic, solution than killing X (and certainly less drastic than power-cycling your computer) is switching to a virtual console (Ctrl-Alt-F1, say), logging in, and killing whichever process is causing problems. That way you don't take everything else down. Alt-F7 (or sometimes F8 if you've had more than one X Server running) will take you back to the graphical environment.

---

### Post by tomkat3 on 2011-07-07
Thanks, this is exactly what I needed! These key strokes aren't quite the internet meme that ctrl+alt+del is, and sometimes its difficult to find out about general stuff like this. This is why we have the forums!:)
The magic keys sound like what I need. When it freezes Ctrl+Alt+F(1-12) have no effect.

---

### Post by robbiemacg on 2011-07-07
I am so glad I read this thread! Those SysRq key combinations are something I'm committing to memory immediately. Useful knowledge for when all else fails.

---

