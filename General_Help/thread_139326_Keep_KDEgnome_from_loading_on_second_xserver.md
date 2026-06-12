---
title: "Keep KDE/gnome from loading on second xserver"
date: 2006-03-03
forum: General Help
---

### Post by pelle.k on 2006-03-03
I use a second xserver on my tv, watching movies and such using mplayer. The problem i get a second kde/gnome session on this second xserver as an unwanted bonus. This is mostly ok with kde, but gnome doesn't like this at all. (they both have a tendency to place tray icons and programs on the second xserver... stupid)
Is there a way to load kde/gnome on my primary xserver, and just activate the second but not really start a WM on it? (or at least start a very very minimal WM on it...?)

---

### Post by pestilence4hr on 2006-03-03
Are you really running two xservers, or just one with two heads?  If you are truly running two xservers, the solution is trivial...run fluxbox or blackbox or icewm or...(pick your favorite lightweight windows manager) on the second xserver.  Picking the WM for the second xserver is identical to the procedure for picking the WM for the first xserver.

If you are just running two heads on one xserver, which is what I suspect (can you move the mouse from one screen to another?  if so, you are running one xserver), then I don't know what to tell you :)

---

### Post by pelle.k on 2006-03-04
Thanks for your reply pestilence4hr!

I think you're right. I've mapped one screen to the right of my primary screen in my xorg.conf (using one graphics card). No xinerama. This way my tv can have a separate resolution than my primary display.

I then launch mplayer using "DISPLAY=:0.1 mplayer -f movie.avi".

So if noone knows how to load another WM on the other head, how do I go about launching a separate xserver on my TV then?

---

