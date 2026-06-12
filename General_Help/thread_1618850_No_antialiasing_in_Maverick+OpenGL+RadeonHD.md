---
title: "No antialiasing in Maverick+OpenGL+RadeonHD"
date: 2010-11-11
forum: General Help
---

### Post by bitwiseshiftleft on 2010-11-11
This may be an overly specific question, however:

I'm running Maverick on a 64-bit machine with a Radeon HD 5750 GPU.  I had Maverick's default version of fglrx installed, but in an attempt to resolve this issue, I've updated to the x-swat PPA version, which made no difference.

My problem is, OpenGL programs (glxgears, fgl_glxgears, pyglet apps, etc) do not run with anti-aliasing.  OpenGL programs set with samples=4 (eg) report having 4xAA, but are not in fact anti-aliased.  I tried forcing AA in the Catalyst control center.  The setting makes no difference.  CCC is working, though, because the vsync options (for example) are applied immediately and do make a difference.

Other things on the system (fonts, inkscape, etc) have AA working just fine.

I just started developing a program which uses OpenGL, so I don't know if the issue is recent or not.

Any advice?  Has anyone else seen this issue?

Thanks in advance!

---

### Post by bitwiseshiftleft on 2010-11-11
Hm.  The issue appears to be tied to compiz.  With Visual Effects turned off, it goes away.

---

