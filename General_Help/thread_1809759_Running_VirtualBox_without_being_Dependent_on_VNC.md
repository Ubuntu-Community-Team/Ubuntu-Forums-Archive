---
title: "Running VirtualBox without being Dependent on VNC"
date: 2011-07-22
forum: General Help
---

### Post by c3ntury on 2011-07-22
I currently run VNC with Gnome to run VirtualBox for my VPS's, but the problem I'm facing is that occasionally, the VNC session will die. 

Ubuntu - 11.04 Server Edition.

I mean, randomly just die and then through up an error (specially connection refused 10061). The problem caused by this is that after I reset the VNC session, VirtualBox will have stopped and in turn the VPS's.

Is there any way I could run VirtualBox without being dependent on VNC + Gnome? Or at least, beable to stop VNC is dying on me?

If you require any more information, just ask and I'll reply within 5 minutes.

Thanks,
Cameron

---

### Post by HermanAB on 2011-07-22
Uhmmm, you don't need VNC at all, ever.  It is mostly Windows thing, so don't expect VNC to work any better than your typical Windows thing...

Use SSH with X forwarding to connect to a distant server.  You can launch a VB client OS without running the VNC GUI - there are command line utilities for that.  Once the VNC client OS is running, you can connect to it using SSH same as if it was a separate physical machine.

So, forget about VNC.  It is a POS and a security risk.  You don't need it.

---

