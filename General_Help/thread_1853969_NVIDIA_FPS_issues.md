---
title: "NVIDIA FPS issues"
date: 2011-10-03
forum: General Help
---

### Post by pwnjangles on 2011-10-03
Ubuntu doesn't seem to like my graphics card. I tried Ubuntu 10.04 - 11.04 and all driver versions and still get horrible frame rates (I think) When I try to play games they run perfect untill I get into actual gameplay then everything just skips a lot. This happens not only in Wine but in Linux native clients too such as Savage2 and Heros of Newerth but Minecraft runs perfect.

These games run flawless on windows of course so is there anyway to fix this?
I already tried running in classic (no effects), turning off compiz, turning off vsync, pretty much doing everything to increase performance and nothing seems to work.


NVIDIA GeForce 7050 / NVIDIA nForce 610i
Pentium(R) Dual-Core  CPU

---

### Post by WasMeHere on 2011-10-03
Just to be sure, have you installed the proprietary driver for nvidia?
But still have a slow system :-(
You are not alone. On my machine with an nvidia chip xp is faster also for 1080/50p high definition video. But I get satisfactory playback with gpu acceleration. Generally I think that games with high video demands are made for windows, and perform better there. So far.

---

### Post by pwnjangles on 2011-10-03
Hmm I think mine was meant for Vista only because XP and 7 run like garbage aswell. :|

---

### Post by WasMeHere on 2011-10-03
Just to be sure, have you installed the proprietary driver for nvidia? Run ```
glxinfo | grep OpenGL
``` and post the result.

---

### Post by pwnjangles on 2011-10-10
Sorry was away for a few days.

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7050 / nForce 610i/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 270.41.06
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:

---

### Post by pwnjangles on 2011-10-10
Tested a few games:
Savage 2 (low settings) linux client lag/skips.
Heros of Newerth (low settings) linux client lag/skips.
WoW (on high settings) under wine runs perfect.
Minecraft linux client runs perfect.

I seem to only have the laggy frame skipping problems on native linux games. :[

---

