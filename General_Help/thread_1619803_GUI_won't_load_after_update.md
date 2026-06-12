---
title: "GUI won't load after update"
date: 2010-11-12
forum: General Help
---

### Post by Citizen Snips on 2010-11-12
I installed a load of recommended updates yesterday and shut down my system last night. Tried to start it again this morning and it won't load for me. The wallpaper appears, but no GUI (no top or bottom bars) and no cursor. The only thing I've managed to do is Ctrl+Alt+Del to open the hibernate/shut down/reboot options.
Any ideas? :confused:

---

### Post by sikander3786 on 2010-11-12
Logout using that Ctrl + Alt + Del dialogue box and select Failsafe Gnome under Sessions after you click your username.

It might be related to compiz.

On the desktop without panels, press Alt + F2, does Application Launcher pop up? If yes, type

```
metacity --replace
```

Does that help?

---

### Post by Citizen Snips on 2010-11-12
The Ctrl+Alt+Del dialogue doesn't give a log out option.

Alt+F2 does nothing, but pressing Ctrl+Alt+F2 (or, apparently, any F-key) switches to a black screen and, after asking for my login information, runs what appears to be a standard terminal. cd and ls commands work, anyway. I tried 'metacity --replace' there, but got the error message
"Window manager error: Unable to open X display".

Probably should have mentioned I'm running Lucid.

---

