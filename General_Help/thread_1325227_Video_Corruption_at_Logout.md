---
title: "Video Corruption at Logout"
date: 2009-11-13
forum: General Help
---

### Post by Akita on 2009-11-13
Just checking if anybody else has seen this before filing a bug report.

Asus N51 laptop with an nVidia m240GT discrete video card (~ 9600GT). Runs perfectly on startup. Play games, browse, desktop effects, etc. No issues at all. The second I logoff, suspend, hibernate, shut down or change to a terminal (ctl-alt-f1) the video gets corrupted. It looks like the screen is frosted glass. Fonts are very jagged. To anybody old enough to remember broadcast television, it looks like a crappy/mis-aligned antenna. This does NOT go away by going back to the GUI. Flipping through video modes, resolutions and what-not has no effect. A full reboot (or a return from a hibernate which amounts to the same thing to the video card) is the only cure I've found. I've tried with and without desktop effects enabled. I've tried 180 and 190 drivers. I've tried killing off frame buffers. I'm so used to having OpenGL/3D/Compiz/GUI issues that I'm at a loss for what's causing switching to tty mode to corupt video that stays broken until the card is reset.

Any ideas before I throw cold water on the nVidia, xorg, uspalsh, everybody else devs? :P

---

