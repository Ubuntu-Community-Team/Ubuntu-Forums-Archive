---
title: "Remote Desktop (VNC) resolution without monitor"
date: 2010-10-19
forum: General Help
---

### Post by tombert on 2010-10-19
Hi all,

Ubuntu Desktop 10.10 boots with disconnected monitor with a screen resolution of 1024x786 ... which in fact is great - other distributions won't even boot ...

How can I change this resolution? ... cause I'am operating my system via VNC and preferably set it to something higher.

thx

---

### Post by HermanAB on 2010-10-19
Howdy,

Simple really.  Kill VNC and use SSH instead:
$ ssh -C -c blowfish user@server gnome-panel

Any program launched from the remote panel will run on the local desktop transparently.  VNC should not be lightly discarded though - it should be thrown, with great force.

---

### Post by tombert on 2010-10-20
thx for trying but:
** (gnome-panel:2096): WARNING **: Cannot register the panel shell: cannot connect to the session bus.

I believe the reason is I don't have a monitor connected ...

---

### Post by tombert on 2010-10-20
Solution:
put the following command into your autostart/profile/whatever:
xrandr --size 1280x1024

---

