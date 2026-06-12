---
title: "Need advice about remote desktop"
date: 2010-10-26
forum: General Help
---

### Post by kjartani on 2010-10-26
Hello.
I want to setup a remote desktop server (VNC or similar) on my 64b Ununtu Maverick and the client on a winXP.

Any recomendations?

Have tried the free VNC from VNC.com but are getting problems with "libstdc++2.10-glibc2.2" for what I cant find any solution.

Maybe a silly question? But can any vnc's even not the original one get connected to any vnc server?

Regards

Kjartan Iversen

---

### Post by Wayne_V on 2010-10-26
I've always like tightvnc -- and it's available in the repo:

$ apt-cache search tightvnc

---

### Post by kjartani on 2010-10-26
What about vnc client for winxp.
Will any vnc client match?
Kjartan

---

### Post by Wayne_V on 2010-10-28
You can use any VNC compatible viewer, or just use connect to the server using a browser and use the built-in java applet.  You can install TightVNC on you winXP machine and use the tightVNC viewer if you don't already have one:

[http://www.tightvnc.com/winst.php#start_view](http://www.tightvnc.com/winst.php#start_view)

---

### Post by linux-hack on 2010-10-28
you can try teamviewer ... it works on linux/win/MAC

---

