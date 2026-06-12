---
title: "Smokin' Guns not working"
date: 2010-09-19
forum: General Help
---

### Post by wilbuzz2 on 2010-09-19
so i got smokin guns but whenever i try to open it in the terminal this what happens.UID 1000 EUID 1000
SG 1.0 linux-i386 Dec 31 2008
----- FS_Startup -----
pak0 has checksum 2206249363
alamo1 has checksum 3611996451
joekarimat1 has checksum 891991440
sg_maps0 has checksum 3111238755
sg_pak0 has checksum 2450671269
sg_sounds has checksum 1404357192
sg_textures0 has checksum 3110057026
Current search path:
/home/neo/.smokinguns/smokinguns
./smokinguns/sg_textures0.pk3 (1018 files)
./smokinguns/sg_sounds.pk3 (278 files)
./smokinguns/sg_pak0.pk3 (803 files)
./smokinguns/sg_maps0.pk3 (161 files)
./smokinguns/joekarimat1.pk3 (178 files)
./smokinguns/alamo1.pk3 (14 files)
./smokinguns
/home/neo/.q3a/smokinguns
/home/neo/.smokinguns/baseq3
./baseq3/pak0.pk3 (107 files)
./baseq3

----------------------
2559 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading opengl32: QGL_Init: Can't load opengl32 from /etc/ld.so.conf: opengl32: cannot open shared object file: No such file or directory
failed
...loading libGL.so: QGL_Init: Can't load libGL.so from /etc/ld.so.conf: libGL.so: cannot open shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
ive installed every open gl thing possible
heres a screeenshot[ATTACH]169965[/ATTACH]:confused:

---

### Post by stinkeye on 2010-09-20
This solved it for me.In the terminal...```
sudo apt-get install libopenal1
sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
```

---

### Post by wilbuzz2 on 2010-09-23
thx worked but i cant turn the graphics down

---

