---
title: "a4tech keyboard and mouse doesn't properly work in games"
date: 2011-02-27
forum: General Help
---

### Post by Lain_13 on 2011-02-27
Hi,

I've tried to search for similar problem on the web and especially here but seems like I can't find solution by myself. So, I've decided to ask for help.

Hardware:
I have A4TECH wireless minikeyboard GLS-6 + mouse G7-630 (comes as keyboard+mouse set with single USB so called 'nano' adapter).

Software:
Ubuntu 10.10
For video I've tried both fglrx and radeon drivers but seems like it doesn't matter.

Old problem:
When I activate keyboard leftclick stops working. Well, it was solved by installation of xorg-...-udev from edgers PPA and then later I've downgraded it to stable updated version where this bug was fixed. So, right now mouse and keyboard works almost fine. Almost because I have different bug.

Current problem:
In games (and only in games!) I have weird bug with controls. Seems like button UP and LEFT pressed forever and character goes in this direction. When I press bottom+right it just stops. I can reproduce this in: PCSX emulator (with GRANDIA for example, installed from PPA), Jasper's Journeys (beta linux version released few days ago), Aquaria (linux version from Humble Indie Bundle). Actually with Aquaria I can't control mouse movements as well. It periodically (with small interval) jumps back to "default" buttons. For example it's button "NO" for "exit game". So, even quitting from this game is tricky. All these games completely unplayable in this state.
On the other side native Eschalon Book I works just fine without any issues.

Why I think it's keyboard/mouse problem?
1. I already had problem with these keyboard/mouse before updated xorg to latest stable version.
2. All these games works fine on my old wireless keyboard/mouse set (not from A4TECH, BTW). As soon as I replace new keyabord/mouse with old set and restart the game problem disappears.

So, is there any way to make this A4TECH's set works properly in native Linux games?

---

### Post by Lain_13 on 2011-02-28
Ummm… so, any ideas what's wrong?

---

