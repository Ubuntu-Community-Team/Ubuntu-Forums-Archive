---
title: "Intel GMA 965 Problem in Ubuntu Lucid"
date: 2010-05-15
forum: General Help
---

### Post by exclinux on 2010-05-15
Hi everyone..
2 days ago i installed **ubuntu** lucid amd64 in my laptop **Compaq  Pressario V3700 inside windows**..and i installed **wine**..**.but  when i open game**...like **warcraft** ,** counter strike, etc**...the  graphic is very lag...anyone know how to solve it?is it related to **Open  GL**?

---

### Post by ilovelinux33467 on 2010-05-16
i think its just the graphics card. My netbook has a Intel GMA 950 and it too plays games slow

---

### Post by arhatsage on 2010-05-16
I'm not totally sure it's just the card--- I have the same chipset and I can't coax OpenGL into working at all, at least with wine. I get the following error: 

"Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.

I definitely have the needed packages installed, and I'm using the i915 driver. Are there known issues with this chipset (and the X3100) in 10.4?

---

