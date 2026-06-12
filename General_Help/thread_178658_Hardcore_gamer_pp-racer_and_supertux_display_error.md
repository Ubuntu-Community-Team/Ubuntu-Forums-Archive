---
title: "Hardcore gamer: pp-racer and supertux display errors"
date: 2006-05-18
forum: General Help
---

### Post by zugu on 2006-05-18
Whenever I try to start ppracer, the following error occurs:

```
zugu@ubuntu:~$ ppracer
PPRacer 0.3.1 --  http://racer.planetpenguin.de
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See http://www.gnu.org/copyleft/gpl.html for details.

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
*** ppracer error: Couldn't initialize video: Couldn't find matching GLX visual (Success)
Segmentation fault
zugu@ubuntu:~$
```and the applicaion crashes. I encountered something similar in supertux:

```
zugu@ubuntu:~$ supertux
Datadir: /usr/share/games/supertux
Warning: Unable to open the file "/home/zugu/.supertux/config" for read!!!

Warning: I could not set up audio for 44100 Hz 16-bit stereo.
The Simple DirectMedia error that occured was:
No available audio device

Warning: No joysticks are available.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Error: I could not set up video for 640x480 mode.
The Simple DirectMedia error that occured was:
Couldn't find matching GLX visual
```I'm not concerned about the joystick and sound errors (there is no joystick and the sound was probably used by some other application). I need to fix the display problems and the permission issue with supertux.

I have nvidia-glx drivers installed (nvidia-setings is not installed, as my video card is RivaTNT2 / 32 MB and I think there is no need for further tweaking).

This issue might also be the reason stellarium and celestia won't work too.
Any help is welcome :)

---

### Post by Steven_B on 2007-03-06
Do you get the same error when you try "glxgears"?
Are you using XGL/Compiz/Beryl?
Could you post your /etc/X11/xorg.conf file?

---

