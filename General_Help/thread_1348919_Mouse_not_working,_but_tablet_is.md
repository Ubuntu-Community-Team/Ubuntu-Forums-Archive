---
title: "Mouse not working, but tablet is"
date: 2009-12-07
forum: General Help
---

### Post by Pansartax on 2009-12-07
So i have a HP tx2000 tablet PC with a Wacom tablet built in. upon installing karmic the wacom works perfectly, but it seems to be overriding my mouse and touchpad since niether of those work.
This is a completely clean install, i have installed no drivers pertaining to my problem.

also, sudo cat /dev/psaux shows they are working perfectly.

Thankful for any help..

---

### Post by Pansartax on 2009-12-08
No ideas?

Would removing wacom help?

---

### Post by Favux on 2009-12-08
Hi Pansartax,

Welcome to Ubuntu Forums!

Usually it's the other way around.  Since the wacom.fdi is numbered 10 and the Synaptic .fdi 11, the Synaptic .fdi runs after the wacom one.  It's almost always Synaptic grabbing things inappropriately.

I doubt it's Wacom causing the problem.  What mouse are you plugging in?  I assume it's a portable usb type.  It could be X doesn't know whether to designate the pad or the mouse the core pointer.

You should take a look at:
```
xinput --list
```
and your lshal:
```
lshal>Pansartax_lshal.txt
```
and see if you can tell what's going on.
Looking at your Xorg.0.log in /var/log/ will also probably be helpful.

---

