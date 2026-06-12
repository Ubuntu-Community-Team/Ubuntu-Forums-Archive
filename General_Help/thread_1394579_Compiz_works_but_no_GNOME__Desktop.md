---
title: "Compiz works but no GNOME / Desktop"
date: 2010-01-30
forum: General Help
---

### Post by sdlynx on 2010-01-30
I just added a new user on my system, and I configured compiz (along with some other things like conky and appearance).  I rebooted the computer and when I log in with that user, it loads my wallpaper and mouse, and I can even move around the desktop cube, but desktop icons don't load, neither does anything else.  What's going on??  No other users are having this problem on my system.

Thanks in advance,
SDLynx

---

### Post by sdlynx on 2010-01-31
bump. I seriously would like to fix this...

---

### Post by gslug79 on 2010-01-31
Hello,

I can think of two possible causes of this problem. One is that Nautilus is not set to display desktop icons. Try opening gconf-editor, type ```
gconf-editor
``` in a terminal, navigate to apps, nautilus, preferences and check that show desktop is enabled.

The other cause could be Compiz being set to draw the walpaper. Open compizconfig-settings-manager in System, Preferences, Desktop effects - this isn't installed by default so you may need to install it first. Find the option for Compiz to draw the wallpaper and if it is enebled, disable it.

Hopefully one of the above works.

---

### Post by sdlynx on 2010-01-31
I tried both of those things, and neither are the problem.  Did I mention I cannot do anything whatsoever aside from move around my cube when I log in (along with see the background and mouse).  Failsafe GNOME is even worse, I can do nothing at all except look at the background and move the mouse.  The xterm session works, if it's any help.

EDIT: Well, it appears I've fixed it.  The problem?  The icon theme I had set.  When I changed that, everything fixed itself.  Wow...

---

