---
title: "3D games won't load (Ubuntu 10.10)"
date: 2010-10-09
forum: General Help
---

### Post by Elcarc on 2010-10-09
Sorry if this is in the wrong place. 

I used to play games on Ubuntu all the time, but since an upgrade or 2 ago, I can't run any game dealing with 3d. Like, it won't even respond when clicked on. I tried to run Warsow from the terminal and got this 
```
edward@edward-desktop:~$ warsow
Added pk3 file /usr/share/games/warsow/basewsw/data0_05.pk3 (1090 files)
Added pk3 file /usr/share/games/warsow/basewsw/data0_05pure.pk3 (1331 files)
Added pk3 file /usr/share/games/warsow/basewsw/editortextures.pk3 (20 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wamphi1.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wamphi2.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wbomb1.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wbomb2.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wca1.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wca2.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wca3.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf1.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf2.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf3.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf4.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf5.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf6.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm1.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm10.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm11.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm12.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm13.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm14.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm15.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm16.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm17.pk3 (4 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm18.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm19.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm2.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm20.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm3.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm4.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm5.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm6.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm7.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm8.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm9.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/models_nate.pk3 (22 files)
Added pk3 file /usr/share/games/warsow/basewsw/modules_05.pk3 (16 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_36.pk3 (28 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_baxandall.pk3 (35 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_billboard.pk3 (14 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_blx.pk3 (328 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_blxbis.pk3 (112 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_cha0swsw.pk3 (90 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_ecel.pk3 (197 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_etr.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_exwsw.pk3 (185 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_factory.pk3 (88 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_fakeads.pk3 (17 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_format.pk3 (22 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_hazelh.pk3 (92 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_hexagons.pk3 (47 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_jewels.pk3 (8 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_melee.pk3 (12 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_nature.pk3 (7 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_refly.pk3 (48 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_russus.pk3 (9 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_solidfake.pk3 (8 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_supersymmetry.pk3 (15 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_terrain.pk3 (8 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_wsw_adverts.pk3 (61 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_wsw_cave1.pk3 (25 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_wsw_city1.pk3 (138 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_wsw_flareshalos.pk3 (21 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_zone_neutre.pk3 (9 files)
Using /home/edward/.warsow-0.5 for writing
Executing: default.cfg
Couldn't execute: config.cfg
Couldn't execute: autoexec.cfg
fs_basepath is write protected.
fs_usehomedir is write protected.
Hostname: edward-desktop
Alias: localhost6.localdomain6
Alias: localhost6
IP: 192.168.2.2
IP: 127.0.0.1
IP: 127.0.1.1
------- angel script initialization -------
Loading angelwrap module.
Loading angelwrap failed
Game running at 62 fps. Server transmit at 20 pps
Console initialized.

----- R_Init -----
Using libGL.so.1 for OpenGL...Display initialization
..XFree86-VidMode Extension Version 2.2
..XFree86-Xinerama Extension Version 1.1
********************
ERROR: Received signal 11

********************
Error: Received signal 11

```

I've reinstalled my drivers an stuff like that, but it seems that didn't work. I have no idea what to do (I'm still really new to linux). :cry:

---

### Post by Elcarc on 2010-10-09
Oh, nevermind, I've fixed it. I just had to delete fglrx again.

---

