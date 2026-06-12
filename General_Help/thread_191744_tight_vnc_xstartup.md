---
title: "tight vnc xstartup"
date: 2006-06-07
forum: General Help
---

### Post by lostdata on 2006-06-07
my xstartup reads

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

________


I am trying to get it to run gnome but all i see is a grey screen when i log in, am i missing something?

thanks

---

### Post by scxtt on 2006-06-07
shouldn't "gnome-session" be in there somewhere?

---

### Post by lostdata on 2006-06-08
[QUOTE=scxtt]shouldn't "gnome-session" be in there somewhere?[/QUOTE]
ya thats kinda what i though too

---

### Post by scxtt on 2006-06-08
[QUOTE=lostdata]ya thats kinda what i though too[/QUOTE]try this:```
xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &
```and see what happens ... from what i can remember when i was doing something similar in the past, i edited the default file and just replaced 99% of it w/ startkde (to start kde) ... now i just use vncserver, which just starts gnome for me by default (of course, i only have gnome installed, so ...)

---

