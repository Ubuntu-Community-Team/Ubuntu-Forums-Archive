---
title: "Freezing on laptop and no idea why"
date: 2011-09-06
forum: General Help
---

### Post by WikedX on 2011-09-06
Okay well it froze while I was actually trying to type this so I'll make it quick in case it happens again

11.04 XFCE running Compiz.
Laptop is a thinkpad x120e with specs though should be perfect for this.
It cant be hardware since Windows 7 never crashes on it
I don't have any idea what could be causing it. The laptop is cool and doesnt overheat. 

I don't know why but I feel like it might be compiz related. I'm using atis video drivers if that makes a difference too.

I'm going to keep my system monitor open for when it happens next and I'll report with that info then, but if you have any suggestions till then it would be nice

---

### Post by jfed on 2011-09-06
Yeah I thought it might be compiz related as well, or x-related. Next time it freezes, try doing both these two things.

Press Ctrl+Alt+Backspace that keystroke restarts the x-server, which is the GUI.

Try pressing Ctrl+Alt+F2, that switches from the current TTY to another, where you wont have the x-server running. (You can press any F key from 1-6, not just 2.)

Also try disabling compiz as well lol, maybe try that first.

---

### Post by WikedX on 2011-09-06
> **jfed said:**
> Yeah I thought it might be compiz related as well, or x-related. Next time it freezes, try doing both these two things.

Press Ctrl+Alt+Backspace that keystroke restarts the x-server, which is the GUI.

Try pressing Ctrl+Alt+F2, that switches from the current TTY to another, where you wont have the x-server running. (You can press any F key from 1-6, not just 2.)

Also try disabling compiz as well lol, maybe try that first.

I think you mean control alt f1? Anyway yeah control alt backspace didnt work and I didnt think to try f1. 

And the issue with disabling compiz is it crashes randomly, so I wouldn't know if that actually fixed the issue or not

---

### Post by jfed on 2011-09-06
> **WikedX said:**
> I think you mean control alt f1? Anyway yeah control alt backspace didnt work and I didnt think to try f1. 

And the issue with disabling compiz is it crashes randomly, so I wouldn't know if that actually fixed the issue or not

No I mean F2 lol. It doesn't matter which TTY you switch to, Ctrl+Alt+F1-6 works. How is it crashing randomly an issue that will stop you from disabling it? It can't crash if it's not running, haha. Try temporarily uninstalling it then.

---

