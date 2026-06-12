---
title: "X11 error with ATI Radeon x2300"
date: 2009-07-20
forum: General Help
---

### Post by barath on 2009-07-20
Hi,
I use Kubuntu 8.10 and my fglrxinfo is like this

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X2300
OpenGL version string: 2.1.8201 Release

glxinfo |grep rendering 

directrendering :yes


but when I type glxgears

10170 frames in 5.0 seconds = 2033.898 FPS
10695 frames in 5.0 seconds = 2138.988 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 129 requests (128 known processed) with 0 events remaining.

I get that can you pls help me .....

---

### Post by ajgreeny on 2009-07-20
So what is the actual problem?  If you are just worried about the error when you stop the gears window, I don't think it is of any consequence, and 2000+ fps is jolly good going.  I always get that error with my ATI 9200SE card with the open source ati/radeon driver running, not fglrx, but the system does everything I need it to, so I've never thought to even question it.

---

### Post by MattPhillips on 2009-07-20
Hi,

This error is quite common--

[http://ubuntuforums.org/showthread.php?t=1032627&highlight=xio+server+error+10](http://ubuntuforums.org/showthread.php?t=1032627&highlight=xio+server+error+10)

As for why bother worrying, it's because you can never tell when/where a flaw in the system will manifest itself.  Things seem fine now, but what about the next application, when, say, one is working under a deadline?  At the very least it would be nice to know what the issue is--i.e. *what* resource is unavailable.

Matt

---

