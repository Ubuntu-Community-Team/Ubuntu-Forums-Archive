---
title: "need to start 2 apps on system startup"
date: 2010-10-28
forum: General Help
---

### Post by npereira on 2010-10-28
Hi,
 
been trying this for a few days now and nothing seems to get the apps started.
 
I need to start vboxwebsrv and x11vnc on startup with a specific username.
 
I tried entering the commands in rc.local as:
 
/bin/su -c "/x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800" user1
 
/bin/su -c "/usr/bin/vboxwebsrv -b" user2
 
But this does not start the app on startup.
 
Can someone tell me what I'm doing wrong?
 
Thanks

---

### Post by matt_symes on 2010-10-28
Hi

Did you make  the script executable?

Kind regards

---

### Post by npereira on 2010-10-28
i found out that they did not complete correctly as I did not have the & at the end of the command.... 
 
Now everything works...
 
Thanks anyway

---

