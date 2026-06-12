---
title: "Blender won't start"
date: 2011-11-09
forum: General Help
---

### Post by MetallicM on 2011-11-09
Hi...

I'm a medialogy student and we are learning animation in maya, however blender has a much better overview, so i desided to install blender in Ubuntu using the software center off course. But i wouldn't start.
In the terminal it posts this message:

> Info: Config directory with "startup.blend" file not found.
Xlib:  extension "GLX" missing on display ":0.0".
/build/buildd/blender-2.58-svn37702/intern/ghost/intern/GHOST_WindowX11.cpp:194: X11 glXQueryVersion() failed, verify working openGL system!
initial window could not find the GLX extension, exit!Please help..

Thanks in advance

---

### Post by mcduck on 2011-11-09
What kind of graphics card you have, and if it's a recently new Ati or nVidia one have you installed the drivers for it?

Blender requires proper OpenGL support to run and that error would indicate you don't have that at the moment.

---

### Post by masonswanson on 2012-11-01
I Am Also HAving This Exact Same Problem In 12.10, And Did Not Have The Problem Before Upgrading From 11.04

---

