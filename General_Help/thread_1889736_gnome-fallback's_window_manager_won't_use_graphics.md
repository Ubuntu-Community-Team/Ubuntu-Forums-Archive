---
title: "gnome-fallback's window manager won't use graphics card acceleration!"
date: 2011-12-01
forum: General Help
---

### Post by Exüberance on 2011-12-01
So I just got my System76 computer, and it works great with one exception: the window manager is EXTREMELY laggy.

It's so bad, that if I set my terminal to have a transparent background, and try to move it, the entire display hangs for literally a second before updating.

To make sure the graphics card drivers were working properly, I opened up 0 A.D. and loaded a map with lots of water. It ran smoothly and looked absolutely amazing on my new card :D

So clearly, the graphics card is working otherwise I would've have even been able to move the camera in 0 A.D.

I want to use gnome-fallback (I gave Unity a try and I absolutely  HATED it- so using Unity is not an option), but it doesn't seem to want to use my graphics card for updating windows. (Or there's some other bug causing it to be extremely slow)

My graphics card is a GeForce GTX 560M, and I'm running gnome-fallback with Compiz.

---

### Post by Exüberance on 2011-12-01
UPDATE: It seems to be a massive bug with Compiz
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/760814?comments=all](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/760814?comments=all)

In my experience with Ubuntu, I've had nothing but trouble with Compiz. Looks like I'll have to switch to another window manager.

Problem "solved" by switching from Compiz to Mutter. To do this:
1) Install mutter from synaptic
2) Edit your **/usr/share/gnome-session/sessions/gnome-classic.session** file replacing the lines
```
RequiredProviders=windowmanager; notifications;
DefaultProvider-windowmanager=gnome-wm
```
with
```
RequiredProviders=windowmanager;
DefaultProvider-windowmanager=mutter
```

(Notice I made 2 changes there, not 1. You have to remove the "notifications" to be able to change to another window manager.)

---

