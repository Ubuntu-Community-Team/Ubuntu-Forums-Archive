---
title: "libGL.so.1 link problems"
date: 2010-05-01
forum: General Help
---

### Post by Zeikcied on 2010-05-01
I upgraded to Kubuntu Lucid using the updater (not a CD), and things were mostly smooth.  A few bumps here and there.  But I've run into a bit of an issue.

I have no idea how this happened.  But I seem to have some leftover NVIDIA libraries.

I have the nvidia-current package installed, so my current NVIDIA libraries are in /usr/lib/nvidia-current.  But I have other files in /usr/lib, such as:

libGL.so.1 (points to libGL.so.185.18.36)
libGLcore.so.1 (points to libGLcore.so.185.18.36)
libGLU.so.1 (points to libGLU.so.1.3.070701)

I think the libGLU file is for Mesa/OpenGL, but I assume the others are old NVIDIA libraries.

My problem is that Kubuntu Lucid seems to be looking at the /usr/lib/libGL.so.1 file instead of the one in nvidia-current, as I'm getting errors such as "/usr/lib/libGL.so.1: unidentified symbol: _nv000023gl" when trying to open the Desktop Effects portion of my System Settings.  I kept getting a similar message when Kubuntu tried to start ksmserver, until I renamed the file libGL.so.1~, but it apparently recreated itself.

Given that the libGL.so and libGLcore.so files appear to be old NVIDIA files that shouldn't be there, is it safe to remove them?  Will it make Kubuntu explode?  I want to make sure before I do anything so I don't destroy my system.

---

