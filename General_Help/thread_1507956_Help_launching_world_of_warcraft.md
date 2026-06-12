---
title: "Help launching world of warcraft"
date: 2010-06-12
forum: General Help
---

### Post by moveright on 2010-06-12
system:
ubuntu 10.04 64bit
laptop: nvidia go7150 and 173 drivers



ok, so I've had many issues installing this most of which I have fixed.  I had to manually install all the wow patches.

When I launch the program from the desktop, I click play and nothing happens.

when I launch it from the terminal I get:

```
err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": /usr/lib32/nvidia-173/libGL.so.1: undefined symbol: _nv000131gl
err:module:import_dll Loading library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135

```

I googled it and only found one thing which was talking about recompiling wine from source using superuser access and adding something about openGL in it.

I'm lost.  I won't lie, I'm a linux newbie and while I have figured out most simple things in linux, this is above my head.  Anyone lend a hand?

---

