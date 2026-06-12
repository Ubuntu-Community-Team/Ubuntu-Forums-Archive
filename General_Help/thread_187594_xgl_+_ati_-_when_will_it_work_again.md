---
title: "xgl + ati - when will it work again?"
date: 2006-06-03
forum: General Help
---

### Post by soc on 2006-06-03
i just wonder if i can get xgl and compiz running again.
this time i tried to use this tutorial:
[http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper]("http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper")
but when i start a session by choosing xgl as session type in gdm i get to a normal desktop with metacity and so on, when i try to run  /usr/bin/startxgl.sh
 manually i get:
```
soc@soc:~$ /usr/bin/startxgl.sh

Fatal server error:
Server is already active for display 1
        If this server is no longer running, remove /tmp/.X1-lock
        and start again.

gnome-session: you're already running a session manager

```

i just don't get it, why is it just so difficult?????

---

### Post by soc on 2006-06-03
*bump*
maybe i'm doing something wrong?
i have the newest fglrx drivers from the repository, everything up-to-date, compiz from quinnstorm's repositories.

---

### Post by neo_reloaded on 2006-06-10
Okay, I got ATI FireGL T2 and 128MB video RAM. So, xgl runs without much of a problem. 
The easiest way to get started on XGL + compiz is -
save following script as .Xsession in your home directory ( with +x mod)
#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME
exec gnome-session

------------------------------------------------------------
on GDM Login screen make sure to select Sessions...->Default session. You should be all set.
But One problem I am seeing is Metacity window border gets screwed up with XGL. I can't change the border also, the default one looks ugly.

---

### Post by starkes on 2006-06-10
[http://www.ubuntuforums.org/showthread.php?t=174233](http://www.ubuntuforums.org/showthread.php?t=174233)

thats what i used to get it working on my ati laptop
if your problem is with ati drivers, thats another story.

---

