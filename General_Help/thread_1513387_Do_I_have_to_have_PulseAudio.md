---
title: "Do I have to have PulseAudio?"
date: 2010-06-19
forum: General Help
---

### Post by puzzler995 on 2010-06-19
Do I have to have pulseaudio installed or can I uninstall it and stick with ALSA? I have been having quite a few problems with pulseaudio and it is getting on my nerves and eating up my CPU. In the syslog about every 5 seconds this appears:
```
Jun 19 12:48:05 xxxx-ubuntu pulseaudio[25185]: module.c: Failed to load  module "module-alsa-source" (argument: "device=hw:1,0"): initialization failed.
Jun 19 12:48:05 xxxx-ubuntu pulseaudio[25185]: main.c: Module load failed.
Jun 19 12:48:05 xxxx-ubuntu pulseaudio[25185]: main.c: Failed to initialize daemon.
Jun 19 12:48:05 xxxx-ubuntu pulseaudio[25183]: main.c: Daemon startup failed.
```
This also constanly reappears in .xsession-errors:
```
** (gnome-volume-control-applet:1973): WARNING **: Connection failed, reconnecting...
```
The weird thing is, I still have sound. I have already tried reinstalling pulseaudio, with no avail. This is happening on both GNOME and Xfce.
Thanks,
Puzzler995

---

