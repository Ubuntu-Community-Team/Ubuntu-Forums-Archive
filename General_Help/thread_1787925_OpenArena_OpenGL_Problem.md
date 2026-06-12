---
title: "OpenArena OpenGL Problem"
date: 2011-06-21
forum: General Help
---

### Post by terrykiwi83 on 2011-06-21
When ever I click on OpenArena I get the following error at startup then nothing?

```

GLimp_Init() - could not load OpenGL subsystem
. See /home/terry/.openarena/baseoa/crashlog.txt for details.

```

Here are the contents of the crashlog file

```


ioq3 1.36+svn1933-1/Ubuntu linux-x86_64 Apr  4 2011
----- FS_Startup -----
Current search path:
/home/terry/.openarena/baseoa
/usr/lib/games/openarena/baseoa/pak6-patch085.pk3 (559 files)
/usr/lib/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/lib/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/lib/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/lib/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/lib/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/lib/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/lib/games/openarena/baseoa/pak0.pk3 (1042 files)
/usr/lib/games/openarena/baseoa

----------------------
4722 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL_Init( SDL_INIT_VIDEO ) FAILED (No available video device)
SDL_Init( SDL_INIT_VIDEO ) FAILED (No available video device)
Setting r_mode -1 failed, falling back on r_mode 3
SDL_Init( SDL_INIT_VIDEO ) FAILED (No available video device)
----- Client Shutdown (Client fatal crashed: GLimp_Init() - could not load OpenGL subsystem
) -----
RE_Shutdown( 1 )
-----------------------
GLimp_Init() - could not load OpenGL subsystem

```

My hardware is an nVidia GTX470 and using the drivers from ubuntu 'additional drivers'.

OS - Ubuntu 11.04 x64

Kernel 2.6.38-8-generic

Any suggestions would be appreciated.

Cheers

---

### Post by terrykiwi83 on 2011-06-21
I have also just tried installing the latest nVidia drivers from their website and still the same problem when trying to start game.

---

### Post by terrykiwi83 on 2011-06-22
Anyone able to help ? Please

---

### Post by terrykiwi83 on 2011-06-23
**Bump** anyone any ideas at all?

More information here after trying from terminal

```


terry@COMMODORE:~$ openarena
ioq3 1.36+svn1933-1/Ubuntu linux-x86_64 Apr  4 2011
----- FS_Startup -----
Current search path:
/home/terry/.openarena/baseoa
/usr/lib/games/openarena/baseoa/pak6-patch085.pk3 (559 files)
/usr/lib/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/lib/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/lib/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/lib/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/lib/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/lib/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/lib/games/openarena/baseoa/pak0.pk3 (1042 files)
/usr/lib/games/openarena/baseoa

----------------------
4722 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL_Init( SDL_INIT_VIDEO ) FAILED (No available video device)
SDL_Init( SDL_INIT_VIDEO ) FAILED (No available video device)
Setting r_mode -1 failed, falling back on r_mode 3
SDL_Init( SDL_INIT_VIDEO ) FAILED (No available video device)
----- Client Shutdown (Client fatal crashed: GLimp_Init() - could not load OpenGL subsystem
) -----
RE_Shutdown( 1 )
-----------------------
GLimp_Init() - could not load OpenGL subsystem

```

---

### Post by terrykiwi83 on 2011-06-23
fixed it myself by doing the following:

```


sudo apt-get remove libsdl1.2debain-all
sudo apt-get install libsdl1.2debain-dev


```

Then I went to libsdl.org and downloaded the latest .tar and configure, make, make install and all worked a treat!

---

