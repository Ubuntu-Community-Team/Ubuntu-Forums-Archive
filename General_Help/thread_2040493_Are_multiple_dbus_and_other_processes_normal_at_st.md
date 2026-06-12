---
title: "Are multiple dbus and other processes normal at startup?"
date: 2012-08-11
forum: General Help
---

### Post by WongFuChu on 2012-08-11
I just noticed this, but I feel like this just happened recently because I've never seen this before. In the System Monitor, I noticed that there are multiple processes of dbus-daemon, dbus-launch, gconfd-2, gvfsd, python, and and notify-osd. With the exception of python which has 3 processes at startup, there is one duplicate of the the other processes. I don't remember this happening before, so I'm wondering what may cause it or if this is normal...

---

### Post by hal8000 on 2012-08-11
Yes, they are normal depending on your desktop and application you use.
Dbus communication is used by many apps so this is normal.
I'm using Ubuntu with kde desktop so dont have gvfsd running, but multiple processes is normal.

---

