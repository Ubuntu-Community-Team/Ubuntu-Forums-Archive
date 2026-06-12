---
title: "Installed Lubuntu &amp; LXDE, Now Hangs Up At Shutdown"
date: 2010-11-16
forum: General Help
---

### Post by tacantara on 2010-11-16
A few days ago, I installed the Lubuntu/LXDE packages to try them out.  I like the speed and simplicity of Lubuntu and LXDE, but they're too simplified, not allowing Docky to run because those DEs don't support compositing.

I still want to keep them for those times when I prefer a simple DE and faster boot up than Ubuntu.  However, I've had a problem for the past two days with shutting down or restarting my computer.  The Lubuntu splash screen comes up (regardless of which DE I booted into) when I select the shut down or restart options.  I have observed the splash screen "dots" blink, continuously, but the machine never shuts down.  I end up having to hold the computer's on/off button down until it shuts itself off.  Is there any known bug that is causing the problem?  I haven't yet found anything through searches that'll clarify it for me.

---

### Post by geekforever on 2010-11-29
Hello
I've got the same problem (Lubuntu on Ubuntu Server freezes on log out),
 did you fix this ?

---

### Post by tacantara on 2010-11-29
I removed Lubuntu & LXDE packages, then restarted my computer.  I still had a problem with the computer hanging up at shutdown, so I pressed the ESC key to look at what was happening "behind the scenes."  I found that my computer was still hanging at shutdown because of another program I had installed.  For the life of me, I can't remember what that program was, but once I uninstalled it and rebooted, the problem was solved.

In short, I recommend using the ESC key to look behind the shutdown screen, and see what process is causing the hang up.

---

