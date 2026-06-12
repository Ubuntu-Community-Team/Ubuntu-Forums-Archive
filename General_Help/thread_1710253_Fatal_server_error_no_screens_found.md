---
title: "Fatal server error: no screens found"
date: 2011-03-19
forum: General Help
---

### Post by wlraider70 on 2011-03-19
I'm running a headless server, but I want to start X for a vnc connection (my understanding is that vnc cannot do this)

When i try startx I get a huge message. ending in 

Fatal server error:
no screens found


I have changed and rearranged my /ect/X11/xorg.conf a million ways. I have also run a dpkg - reconfigure command.
I don't care about X is there is another way to get vnc/rdp up.

full error log is attached

---

### Post by wlraider70 on 2011-03-19
I did some working... now i get this



luke@media:~$ sudo startx
xauth:  error in locking authority file /home/luke/.Xauthority
xauth:  error in locking authority file /home/luke/.Xauthority
xauth:  error in locking authority file /home/luke/.Xauthority
xauth:  error in locking authority file /home/luke/.Xauthority


Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.

 ddxSigGiveUp: Closing log


I'm not sure if it running correctly and thats causing the errors.

---

