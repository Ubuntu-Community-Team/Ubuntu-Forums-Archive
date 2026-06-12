---
title: "Nexuiz won't start up"
date: 2010-05-13
forum: General Help
---

### Post by absolutezero1287 on 2010-05-13
I just got a new graphics card. I got an Nvidia GeForce 8400 GS and its working great. Videos are a lot smoother and my overall experience is much better. I figured that I'd test my card to see if it can handle some gaming. 

I installed Nexuiz but it wouldn't start. The screen would just flicker. I decided to see what pops up in the terminal and the error message that most pops up is: "Couldn't find matching GLX visual." Here is the full output.

Any help would be much appreciated.

```

Nexuiz Linux 03:50:47 Oct 25 2009 - debug
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data.pk3 (3664 files)
Added packfile /usr/share/games/nexuiz/data/music.pk3 (18 files)
Added packfile /usr/share/games/nexuiz/data/textures.pk3 (5370 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libogg.so.0" - loaded.
Trying to load library... "libtheora.so.0" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisenc.so.2" - loaded.
Trying to load library... "libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing defaultNexuiz.cfg
execing physics26.cfg
execing ctfscoring-div0.cfg
execing balance.cfg
execing effects-normal.cfg
execing turrets.cfg
execing unit_machinegun.cfg
execing unit_hk.cfg
execing unit_hellion.cfg
execing unit_mlrs.cfg
execing unit_flac.cfg
execing unit_fusreac.cfg
execing unit_plasma.cfg
execing unit_plasma2.cfg
execing unit_tesla.cfg
execing unit_phaser.cfg
execing unit_walker.cfg
execing unit_ewheel.cfg
couldn't exec unit_repulsor.cfg
couldn't exec config.cfg
couldn't exec data/campaign.cfg
execing config_update.cfg
couldn't exec autoexec.cfg
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:0
Client opened a socket on address [0:0:0:0:0:0:0:0]:0
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.13
Using SDL library version 1.2.14
Failed to set video mode to 1024x768: Couldn't find matching GLX visual
Desired video mode fail, trying fallbacks...
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.13
Using SDL library version 1.2.14
Failed to set video mode to 1024x768: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.13
Using SDL library version 1.2.14
Failed to set video mode to 1024x768: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.13
Using SDL library version 1.2.14
Failed to set video mode to 1024x768: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 640x768x32x60hz
Linked against SDL version 1.2.13
Using SDL library version 1.2.14
Failed to set video mode to 640x768: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 640x480x32x60hz
Linked against SDL version 1.2.13
Using SDL library version 1.2.14
Failed to set video mode to 640x480: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 640x480x16x60hz
Linked against SDL version 1.2.13
Using SDL library version 1.2.14
Failed to set video mode to 640x480: Couldn't find matching GLX visual
Quake Error: Video modes failed

```

---

### Post by absolutezero1287 on 2010-05-13
UPDATE: After some googling it seems that many users are experiencing this problem. 

Judging by the output of glxinfo I'd say that something would have to be changed in the Xorg.conf. However, I think that Ubuntu no longer uses one. I think the dri and glx extensions have to be enabled but I'm just speculating.

```

absolutezero@satori:~/Documents$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

```

Another thing I've tried is using the "Nvidia X Server Settings" GUI but it gives me an error message saying the following: "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

However, the Hardware Drivers utility says that I am indeed using the NVIDIA driver. What's going on?

---

### Post by Woody1987 on 2010-05-13
Have you installed the nvidia driver? If not, run

```
sudo apt-get install nvidia-glx-185
sudo nvidia-xconfig

```

Reboot

---

### Post by absolutezero1287 on 2010-05-13
> **Woody1987 said:**
> Have you installed the nvidia driver? If not, run

```
sudo apt-get install nvidia-glx-185
sudo nvidia-xconfig

```

Reboot

Yes, I have the Nvidia driver installed. I've installed the NVidia-current package. As for the driver, according to the Hardware Drivers utility the current one is the recommended one. I tried nvidia-xconfig and the Xorg.conf that it created was extremely sparse. I'll give it a shot anyway and I'll be back with the results.

---

### Post by absolutezero1287 on 2010-05-16
Hey, the nvidia-xconfig worked! Thanks a lot!

---

