---
title: "Frozen Window Title Bar on Desktop"
date: 2010-07-07
forum: General Help
---

### Post by ottabaub on 2010-07-07
I'm running Ubuntu 10.04. I have "roll ups" selected in System->Preferences->Windows and "Automatically remember running applications when logging out" in System->Preferences->Startup Application (Options tab). Yesterday I had a folder window rolled up when I shut down. Today, after booting up, there is a frozen title bar on my desktop which has no buttons and no title. I cannot move it, unroll it or delete it.

Is there a file somewhere that defines what is on the desktop that I can manually edit? Anybody have any ideas how I can delete this thing?

---

### Post by krome! on 2010-12-11
i have this same problem. how the hell do you fix it? it's annoying to two frozen rolled up title bars on one of your workspaces. and if you try removing some workspaces, the windows only move to a new one.

screenshot attached.

---

### Post by ottabaub on 2010-12-12
I haven't had that problem happen again since I posted this message. I've avoided repeating it by not leaving rolled up windows prior to shutting down. I did manage to get rid of the bar but, honestly, I don't remember how.

---

### Post by donoterase on 2011-02-06
I also had this same issue...I noticed that when I killed compiz, the shaded title bar's also disappeared, but upon launching compiz --replace, it comes back!!

I managed to fix the issue by deleting all contents of ~/.config/gnome-sessions folder. I also deleted a few other files as well, but can't remember now, and I don't want to replicate the issue again. I may have also deleted all the compiz folders in ~/.config, ~/.gconf.

---

