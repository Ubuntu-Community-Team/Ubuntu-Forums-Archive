---
title: "Help: Gens OpenGL without GTK"
date: 2006-02-18
forum: General Help
---

### Post by dreadbrazen on 2006-02-18
OK, so I've been working to create an emulation box with advancemenu.  Currently working are advancemame and zsnes.  I can get DGen to work for genesis emulation, but it's too unstable and only works for half of the roms.

I've been able to successfully compile Gens for Linux RC3.5 with OpenGL support.

[http://users.vialink.com.br/denilson/gens/]("http://users.vialink.com.br/denilson/gens/")

It works wonderfully, great speed, sound, visual, etc.  However, I can only compile it with the GTK frontend.  I have been fiddling around with the config and makefiles to get the GUI to NOT install (which was possible in previous versions), but it always installs the GUI anyways.  Can anyone tell me what to do with this makefile to disable the GUI?

(by the way, in order to compile on Ubuntu, you have to remove the "static" on line 787 in /src/gens/emulator/g_main.c)

Any help would be greatly appreciated.

---

