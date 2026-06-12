---
title: "somehow rendered my computer useless, please help"
date: 2011-06-01
forum: General Help
---

### Post by samanthaSeverin on 2011-06-01
I was trying to activate the compiz cube and it was like "do you want to disable the desktop wall?" and I was like yeah and it ended up taking away my ability to minimize and maximize windows and things so I looked up how to fix that and it told me to go to preferences and restore to defaults so I did that and...

now my computer is totally blank. all I have is the desktop background, no icons to click on or anything, cntrl+alt+t doesn't bring up a terminal anymore, I can't get to settings. I have no idea what to do. I only managed to get to this forum by right clicking and creating an icon containing the command "google-chrome".

---

### Post by BlouBlou on 2011-06-01
Did you try loging using the "classic-session" located in GDM menu (in the one you select the user)?

---

### Post by Larkspur on 2011-06-01
> **samanthaSeverin said:**
> I was trying to activate the compiz cube and it was like "do you want to disable the desktop wall?" and I was like yeah and it ended up taking away my ability to minimize and maximize windows and things so I looked up how to fix that and it told me to go to preferences and restore to defaults so I did that and...

now my computer is totally blank. all I have is the desktop background, no icons to click on or anything, cntrl+alt+t doesn't bring up a terminal anymore, I can't get to settings. I have no idea what to do. I only managed to get to this forum by right clicking and creating an icon containing the command "google-chrome".

If you can't log out, create a launcher with the command "compiz --reset" and Unity will come back.

---

### Post by zo3adams on 2011-06-01
some tips that may help:

if cntrl-alt-t doesn't bring up a shell, try cntrl-alt-F1  (or F2, F3.)  That hot key brings you to a terminal shell outside of the GUI (notice now window, no images of any kind) for pure terminal debugging.

Once there, try "sudo gdm restart" or "sudo /etc/init.d/gdm  restart"  to force the graphical interface to restart.

Then ctrl-alt-F7 to return to the graphical shell.

If problem persists, there's a config file somewhere that needs changing, can sue the ctrl-altF# shells to get to it and update it.

---

