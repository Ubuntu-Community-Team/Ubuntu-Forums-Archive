---
title: "Stellarium -"
date: 2011-05-08
forum: General Help
---

### Post by p2cd3 on 2011-05-08
I have installed Stellarium, but am getting this message output:

jack@Binabik:~$ stellarium
Using default graphics system specified at build time:  raster 
 ------------------------------------------------------- 
[ This is Stellarium 0.10.6 - [http://www.stellarium.org](http://www.stellarium.org) ] 
[ Copyright (C) 2000-2010 Fabien Chereau et al          ] 
 ------------------------------------------------------- 
Writing log file to: "/home/jack/.stellarium/log.txt" 
File search paths: 
  0 .  "/home/jack/.stellarium" 
  1 .  "/usr/share/stellarium" 
Attempting to use an existing older config file. 
Config file is:  "/home/jack/.stellarium/config.ini" 
QPixmap::handle(): Pixmap is not an X11 class pixmap
OpenGL supported version:  "1.2 Mesa 7.10.2" 
Qt GL paint engine is:  "OpenGL" 
Cache directory is:  "/home/jack/.cache/stellarium/stellarium" 
Sky language is  "en_CA" 
Application language is  "en_CA" 
Loading Solar System data ... 
Loaded 38 / 38 planet orbits from "/usr/share/stellarium/data/ssystem.ini" 
Loading star data ... 
"Loading "/usr/share/stellarium/stars/default/stars_0_0v0_1.cat": 0_0v0_1; 5013" 
"Loading "/usr/share/stellarium/stars/default/stars_1_0v0_1.cat": 1_0v0_1; 21999" 
"Loading "/usr/share/stellarium/stars/default/stars_2_0v0_1.cat": 2_0v0_1; 151416" 
"Loading "/usr/share/stellarium/stars/default/stars_3_1v0_0.cat": 3_1v0_0; 434064" 
Finished loading star catalogue data, max_geodesic_level:  3 
navigation/preset_sky_time is a double - treating as jday: 2.45151e+06 
Loaded 10051 NGC records 
Loading NGC name data ... 
Loaded 222 / 222 NGC name records successfully 
Loaded 88 / 88 constellation records successfully for culture "western" 
Loaded 85 / 85 constellation art records successfully for culture "western" 
Loaded 89 / 89 constellation names 
Loading constellation boundary data ...  
Loaded 782 constellation boundary segments 
Loading star names from "/usr/share/stellarium/skycultures/western/star_names.fab" 
Loaded 230 / 230 common star names 
Loading star names from "/usr/share/stellarium/stars/default/name.fab" 
Loaded 3215 / 4359 scientific star names 
Creating GUI ... 
stellarium: nv10_render.c:104: get_hw_format: Assertion `0' failed.
Aborted

The splash screen shows for about 5 seconds & goes away - I have an Nvidia card

---

### Post by patrick_the_fat on 2011-05-09
I am having the exact same issue. Are you currently using the Nouveau video card drivers? Also, which version of Ubuntu are you using?  The only solution at this time seems to be to use the default Nvidia drivers.  As far as I know, the Nouveau drivers are still going through major development and are to be considered "experimental" in this case.

---

### Post by M@r on 2011-08-31
Hello, did you guys find a solution? I just installed it and I'm getting a very similar message:

fal@fal:~$ stellarium
Using default graphics system specified at build time:  raster 
 ------------------------------------------------------- 
[ This is Stellarium 0.10.5 - [http://www.stellarium.org](http://www.stellarium.org) ] 
[ Copyright (C) 2000-2010 Fabien Chereau et al          ] 
 ------------------------------------------------------- 
Writing log file to: "/home/fal/.stellarium/log.txt" 
File search paths: 
  0 .  "/home/fal/.stellarium" 
  1 .  "/usr/share/stellarium" 
Config file is:  "/home/fal/.stellarium/config.ini" 
Qt GL paint engine is:  "OpenGL" 
Cache directory is:  "/home/fal/.cache/stellarium/stellarium" 
Sky language is  "en_US" 
Application language is  "en_US" 
Loading Solar System data ... 
Loaded 38 / 38 planet orbits 
Loading star data ... 
"Loading "/usr/share/stellarium/stars/default/stars_0_0v0_1.cat": 0_0v0_1; 5013" 
"Loading "/usr/share/stellarium/stars/default/stars_1_0v0_1.cat": 1_0v0_1; 21999" 
"Loading "/usr/share/stellarium/stars/default/stars_2_0v0_1.cat": 2_0v0_1; 151416" 
"Loading "/usr/share/stellarium/stars/default/stars_3_1v0_0.cat": 3_1v0_0; 434064" 
Finished loading star catalogue data, max_geodesic_level:  3 
navigation/preset_sky_time is a double - treating as jday: 2.45151e+06 
Loaded 10051 NGC records 
Loading NGC name data ... 
Loaded 222 / 222 NGC name records successfully 
Loaded 88 / 88 constellation records successfully for culture "western" 
Loaded 85 / 85 constellation art records successfully for culture "western" 
Loaded 89 / 89 constellation names 
Loading constellation boundary data ...  
Loaded 782 constellation boundary segments 
Loading star names from "/usr/share/stellarium/skycultures/western/star_names.fab" 
Loaded 230 / 230 common star names 
Loading star names from "/usr/share/stellarium/stars/default/name.fab" 
Loaded 3215 / 4359 scientific star names 
Creating GUI ... 
stellarium: nv10_render.c:104: get_hw_format: Assertion `0' failed.
Aborted
fal@fal:~$ 

I'm running [FONT=Verdana][SIZE=1]Ubuntu 11.04 and Stellarium 0.10.5.  I tried with and without the Experimental 3D support for NVIDIA cards[COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C][/COLOR][/FONT][/COLOR][/SIZE][/FONT]

---

