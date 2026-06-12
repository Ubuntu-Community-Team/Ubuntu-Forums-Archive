---
title: "Cairo Dock x64?"
date: 2010-01-30
forum: General Help
---

### Post by Cam! on 2010-01-30
I have 64-bit Ubuntu, and Cairo Dock doesn't work at all. It has a large black box around it. I have my visual effects on max, so Composition isn't a problem. When I simulate Composition/Transparency via the Cairo Dock settings menu, another annoyance happens: I get a black OUTLINE around the dock.


To make a long story short, how do I make Cairo Dock work and look perfect on my 64-bit OS?

---

### Post by fabounet on 2010-01-31
more details please ...

---

### Post by Sub101 on 2010-01-31
Are you running with OpenGL?

---

### Post by Cam! on 2010-01-31
> **Sub101 said:**
> Are you running with OpenGL?

I don't know. I know that my graphics card is an ATI Radeon HD 4850 (512MB), and that it won't recognize compositing, so I have to simulate it through the Cairo Dock settings menu. Because of this, parts of the dock look messed up, and there's a semi-transparent outline near it.

---

### Post by Leppie on 2010-01-31
did you install compiz?
i'm running the cairo dock on a x64 with compiz ;)

cairo dock has 2 entries in the menu, one is "Cairo-Dock (no GpenGL)" and the other one is "GLX-Dock (Cairo-Dock with OpenGL)"

---

### Post by fabounet on 2010-01-31
your card probably supports composite, but composite is not enough to run glx-dock.
and old ATI cards can't run it properly (until the 9600 I think)
so just use the cairo version, you will just loose the fancy effects, anything else works the same.

---

