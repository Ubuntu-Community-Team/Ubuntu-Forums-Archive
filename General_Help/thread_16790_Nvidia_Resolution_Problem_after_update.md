---
title: "Nvidia Resolution Problem after update"
date: 2005-02-23
forum: General Help
---

### Post by kayz on 2005-02-23
Hi,

I am running Ubuntu 4.10
XFree86 version 4
Restricted Nvida Modules installed.

after a recent system upgrade I have lost the ability to change my screen resolution. it is now stuck on 640x480 at 60hz. PS everything worked fine before the upgrade.

which is a real problem for me as the display attached is an LCD panel with a native resolution of 1024X768 (I also suspect that the refresh rate should be 70Hz) So the display is quite hard to read at present.

I have noted that after the smart upgrade Xfree86 complained that the GLCore module could not be found.  However the NVidia Logo is still displayed during X Server startup.

I have not made any manual changes to XFree server configuration. it is at default  installed values (+ changes applied byt the NVidia Modules) these were installed as per the Binary Driver Howto.

What remidial action should I take ?

regards

Konrad.

---

### Post by dude2425 on 2005-02-23
IIRC, GLCore should have been commented out along with DRI in your /etc/X11/xorg.conf file. Try doing that and see if it works out for ya.

---

### Post by kayz on 2005-02-24
Commentign out the relevant lines eliviates the error messages in the log file, however it does not solve the problem. the server is still stuck at the wrong resolution. I have tried manually ediiting the mode lines but this seems to have no effect. :-&

---

### Post by RU63 on 2005-02-26
Check this thread:

[http://www.ubuntuforums.org/showthread.php?p=79371#post79371](http://www.ubuntuforums.org/showthread.php?p=79371#post79371)

Same problem, and a solution!

Peace,

---

