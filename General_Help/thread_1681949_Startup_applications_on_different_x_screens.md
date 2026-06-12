---
title: "Startup applications on different x screens"
date: 2011-02-05
forum: General Help
---

### Post by ingeon on 2011-02-05
How does one go about launching applications at start on a specific xscreen. I searched and found these 2 quotes below telling me that it must be possible (don`t really understand the commands, like to start an app fullscreen [on that specific xscreen]

Example:
If I say use the xfce desktop environment and try adding
> SDL_VIDEO_FULLSCREEN_HEAD=1 DISPLAY=:0.1 program -fs
and/or
> DISPLAY=:0.1 program
under 'session and startup' it does nothing.
I found running either from these in terminal works, however if I create a launcher it gives me 'failed to execute I/O error even if 'run in terminal' is ticked.

Old post hinting its possible
> unzari[QUOTE]Dual X sreens + Gnome sessions + Input device
I have set up dual X screens on my Nvidia card... not TwinView. (I tried that too, but I prefer having separate X screens... no confusion over resolutions between them, and you can explicitly start applications on the display you want.)[/QUOTE]

Using a 17" CRT and 40" LCD.
My xorg contains the Monitor&Screen 0 & 1 settings.

---

### Post by sisco311 on 2011-02-05
In the launcher you have to use **env** to run the application with the environment containing **DISPLAY=:0.1** :

```
env DISPLAY=:0.1 program
```

---

