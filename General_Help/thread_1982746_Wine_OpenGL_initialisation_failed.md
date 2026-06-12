---
title: "Wine OpenGL initialisation failed"
date: 2012-05-19
forum: General Help
---

### Post by doom3d on 2012-05-19
After upgrading from Ubuntu 10.10 to 12.04 the system had two problems:
- awkward screen resolution (800*600 max. on full HD monitor)
- no directX support in Wine, Wine is no longer able to initialize OpenGL

Hardware: ATI Radeon 9200SE 5964 (AGP) RGB out connected LG 32LD465 full HD TV-monitor. 

I managed to solve the screen resolution issue, but run out of ideas with wine. Seems to be an OpenGL initialisation problem.

Changes to the system:
/etc/X11/xorg.conf 
/usr/share/X11/xorg.conf.d/99-vesahack
/etc/gdm/Init/Default

Also attached:
- LG 32LD465 television EDID reading
- Xorg.0.log
- Heroes of Might & Magic 3 run trial 
- xdpyinfo output

Remarks:

EDID reading is incorrect. TV is capable to run at 1920x1080 60 Hz.

 Ubuntu 10.10 worked out of the box, the only change was load "fglrx" option in module section of xorg.conf (just for sure, from previous OS versions), and default color depth set to 16 bit - necessary to run highcolor games in windowed mode.

I have set up modelines using cvt & xrandr and added xrandr lines to /etc/gdm/Init/Default. It worked fine with Ubuntu 11.04, but didn't with 11.10 & 12.04. So I continued with 99-vesahack and a shiny new xorg.conf. Now resolution is ok, but Wine keeps crashing, several versions from 1.3.x to 1.5.4. Tested with several executables and desktop environments. Executables that do not require DirectX are running. (e.g. heroes3 mapeditor runs, heroes3 game crashes)

**UPDATE: **I did this:
sudo apt-get remove --purge fglrx*
sudo apt-get purge xserver-xorg
sudo apt-get install xserver-xorg xserver-xorg-video-all ubuntu-desktop xorg
sudo apt-get install libgl1-mesa-swrast

Now WINE isn't crashing, but unusable- way too slow. Speed around 1 FPS with a game from 1996. Any idea to make it usable?

**UPDATE2:**
After replacing libgl1-mesa-swx11 with libgl1-mesa-glx, now it runs! (practically i have reinstalled & removed again fglrx, and with fglrx came libgl1-mesa-glx)

---

