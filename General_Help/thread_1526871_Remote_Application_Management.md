---
title: "Remote Application Management"
date: 2010-07-08
forum: General Help
---

### Post by Jumbs on 2010-07-08
I am trying to kick off a graphical process remotely but have it run on my desktop at home.

I want to be able to open a program from a remote ssh session (on windows through xming), but have it open on my computer at home and stay running after i shut down the remote session.

I know i can run a process detached from my remote terminal with nohup, but that seems to not work for graphical programs.

I believe it has something to do with setting the DISPLAY env variable to use the other X server, but cannot seem to get it right.


If there is also a better way for doing this, please let me know.
VNC would be perfect, but the connection in play is too slow to use it.

Thanks!

---

