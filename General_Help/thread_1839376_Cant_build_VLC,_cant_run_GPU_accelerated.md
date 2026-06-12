---
title: "Cant build VLC, cant run GPU accelerated"
date: 2011-09-05
forum: General Help
---

### Post by p-r-e-d-a-t-o-r on 2011-09-05
Hi all, I wanted to build VLC on my Ubuntu 11.04. I installed all needed packages bud when i run ./compile or make I get this error:
```
x11/x11_display.cpp:29:21: fatal error: X11/xpm.h: No such file or directory
compilation terminated.
make[6]: *** [libskins2_plugin_la-x11_display.lo] Chyba 1
make[6]: Leaving directory `/home/p-r-e-d-a-t-o-r/Stiahnuté/vlc-1.1.11/modules/gui/skins2'
make[5]: *** [all] Chyba 2
make[5]: Leaving directory `/home/p-r-e-d-a-t-o-r/Stiahnuté/vlc-1.1.11/modules/gui/skins2'
make[4]: *** [all-recursive] Chyba 1
make[4]: Leaving directory `/home/p-r-e-d-a-t-o-r/Stiahnuté/vlc-1.1.11/modules/gui'
make[3]: *** [all] Chyba 2
make[3]: Leaving directory `/home/p-r-e-d-a-t-o-r/Stiahnuté/vlc-1.1.11/modules/gui'
make[2]: *** [all-recursive] Chyba 1
make[2]: Leaving directory `/home/p-r-e-d-a-t-o-r/Stiahnuté/vlc-1.1.11/modules'
make[1]: *** [all-recursive] Chyba 1
make[1]: Leaving directory `/home/p-r-e-d-a-t-o-r/Stiahnuté/vlc-1.1.11'
make: *** [all] Chyba 2

```I need to build vlc because I readed that if I want to enable GPU acceleration on my AMD card I need to rebuilt VLC.Because when I just install xvba-video and play video in vlc it crashed with error:
```
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x2576120] main libvlc: Spustenie programu VLC s predvoleným rozhraním. Pre spustenie bez rozhrania zadajte príkaz 'cvlc'.
Blocked: call to setlocale(6, "")
Warning: call to srand(1315428756)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:3421): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
libva: libva version 0.31.1
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
Chyba segmentácie
```Of course I apt-get remove vlc before I started building. Thanks for every help.[messages][/messages]

---

### Post by themusicalduck on 2011-09-05
Run ```
sudo apt-get install libxpm-dev
``` then try to compile again.

edit: Have you tried using SMplayer? I use it to use hardware acceleration with my NVidia card and everything is there by default. I just have to look through Options > Preferences > Video > Output driver and set it to vdpau. For you I think it would be va-api it needs to be set to.

Might be easier if VLC won't compile.

---

### Post by p-r-e-d-a-t-o-r on 2011-09-05
Thanks now make / make install work but I have still problem with GPU acceleration. When I add video to play VLC crash with output I wrote above.

EDIT: SMplayer I tested but not with vdpau. When I now play video it write "Video filters are disabled when using vdpau".Btw I need GPU acceleration because i have C-50 APU that dont have enough strong CPU to play FUllHD / HD with bigger bitrate. On windows I can play FullHD / HD with BS.Player.

EDIT2: lol I am noob :D I have checked to disable it. But nothing changes.

---

### Post by themusicalduck on 2011-09-05
Have you installed drivers for your APU? I did a Google search and it looks like the C-50 uses the ATI catalyst drivers, so if you haven't yet, find the "Additional Drivers" program and see if you can install anything from there. If you install these it should significantly improve your video playback.

If there is nothing there to install then let me know.

On SMPlayer, there's no need to select vdpau because vdpau only works with NVidia graphics cards. You need to select va-api, which might become an option once your graphics drivers are installed.

---

