---
title: "Black screen, still running"
date: 2010-07-05
forum: General Help
---

### Post by beatme101 on 2010-07-05
I'm getting a peculiar sort of crash. It happens when a Wine program crashes. The program is a game server and runs in a Wine terminal; no graphic.

What happens is, the program crashes for whatever reason (I don't know the exact cause, but the program terminates), and then immediately everything on my screen goes black. However, I still have a cursor, and all other programs that were running continue to run (I can access my other game servers from other computers). The cursor changes icons as I move it around the black screen, as though it is interacting with the programs that are still running. ctrl+alt+f2 still works, so at least I can restart the computer safely.

This is what appears at the end of ~/.xsession-errors:
```

gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on (the first line of which is probably minor)X server :0.0.
evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
** Message: <info>  disconnected by the session bus.

nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Window manager error: Unable to open X display :0.0
```

Xorg's logs don't look very useful in this situation (I wish they had timestamps) but I'm not sure which one would contain my last session.

Here are some of my software versions:
Ubuntu 10.04 x86-64
Wine 1.1.42
nvidia-current (195.36.24-0ubuntu1~10.04)

My hardware:
Intel Core 2 Duo E6550 (2.33 GHz)
Nvidia GeForce 7900 GTO
2 GB RAM

---

### Post by r2rX on 2010-07-05
Well, at the very least, you can configure Wine to function in an emulated virtual desktop. This way, even if such errors/crashes occur, you can simply close the window without having to reset.

Concerning the game you've hosted, how long does it take till it crashes? Is it instant, or is there a time delay?

Also, update to the latest version of Wine (v1.2 rc6). Find out if that helps at all.

r2rX  :D

---

### Post by beatme101 on 2010-07-05
The game only causes this situation when the crash happens early on, during the loading process; a scripting error of my own fault. (It doesn't help that the game is old, unsupported, and just naturally very unstable. But on Windows (through a vm or on an actual windows machine) the crash is usually very clean, program terminates without any fuss. The crashes that don't happen when the program is starting are also clean in this way, even on Linux.)

The game window is not fullscreen, so I kind of doubt a virtual desktop would help. However, the next time my servers are empty (so probably not today) I will try switching to that (and the new version of wine).

If you're wondering, the game is Starsiege: Tribes.

---

