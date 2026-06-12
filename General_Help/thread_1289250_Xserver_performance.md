---
title: "Xserver performance"
date: 2009-10-12
forum: General Help
---

### Post by zx5000 on 2009-10-12
Can you please dump xorg xserver and switch to xfree86 or something that has better performance?

I've been a linux user/evangelist since 2000 and just since XServer became the standard X engine applications like google earth and x-plane have become unusable.

I am sadly going to have to recommend Window XP to my customer who is building a cockpit simulator based on x-plane. 

This is so embarrassing.

---

### Post by kerry_s on 2009-10-12
that makes no sense, they would defiantly not go backwards.
it is most likely not xorg, but your video drivers at fault. 

if xp is what works use it.

---

### Post by 3rdalbum on 2009-10-12
Try using a version of Xorg from after 2006, with 3D graphics acceleration.

---

### Post by zx5000 on 2009-10-12
Backwards? No, xfree86 is still releasing new versions.Really it's the new distros video performance that's going backwards. Fedora introduced this problem between it's versions 8 and 9. As  I understand it the only reason for switching to Xorg was some licensing verbiage change in xfree86 not for technical reasons.

Here are the video drivers I've worked with so far:
ATI Radeon 9200
ATI Radeon 9600 
NVidia Quadro
NVidia GeForce2
Intel 945

Xorg native drivers (part of the standard ubuntu, fedora, etc) are extremely slow.
Proprietary drivers don't build or don't run (ATI Catalyst 9.3 produces multi-colored garbage on the screen)

Just try google earth or x-plane and you'll see what I mean.
GLXGears only produces only 22FPS at 1024x768 fullscreen.

---

