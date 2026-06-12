---
title: "Compiz Fusion"
date: 2009-11-17
forum: General Help
---

### Post by Mthbk1 on 2009-11-17
Is it necessary to have a graphics card so as to enable compiz cube.
The verbose of ubuntu, on trying to start compiz, says that the system is looking for nVidia. I don't have a graphics card but a pretty modest processor (intel core 2 duo 1.86 G) along with one gb RAM. 
Is there a way to enable compiz without the Graphics card?

---

### Post by 3Miro on 2009-11-17
You cannot run a computer without a graphics card, you have a card, probably some low end integrated Intel card.

The real question is, does that low end card support basic OpenGL acceleration. Regardless of how powerful the CPU is, it cannot efficiently support OpenGL. However, more modern Intel video chips do support the required technology. I have seen the cube on an integrated Intel card. The best results, though, would be on an nVidia or ATI.

Check to see what motherboard and what integrated video card you have and/or look for tools to test OpenGL capabilities on your Linux box. With good OpenGL, you should have no trouble dong the cube and all.

---

