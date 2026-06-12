---
title: "X11VNC Hijacks X Server - subsequent boot fails to load GUI"
date: 2012-04-30
forum: General Help
---

### Post by dsauxier on 2012-04-30
I thought I would post this here in case others are having the same trouble.
I'm using 64-bit Xubuntu 12.04

The following notes are from memory - I didn't think to cut-and-paste the errors.  Also, I did not find the error messages anywhere under /var/log

When booting, the Xubuntu splash screen would briefly appear, then the screen would just go dark.

My workaround for this problem was to uninstall X11vnc.
```
sudo apt-get remove x11vnc
```
Again, this is upon boot, so x11vnc shouldn't even be running at this point.

Further details on the problem and steps...

I went to console#1 by pressing all 3 keys at once : 
<CTRL><ALT><F1>
From there I logged in and then ran
```
startx
```
to attempt to launch X manually.

After a while, nothing happened.  I went to a 2nd console window <CTRL><ALT><F2> and killed the "running" X session.
```
ps -ef | grep X
sudo kill -9 enter_the_process_id_here
```

Went back to console#1 and I had got some error messages to the effect : unable to start x server resource temporarily unavailable

---

