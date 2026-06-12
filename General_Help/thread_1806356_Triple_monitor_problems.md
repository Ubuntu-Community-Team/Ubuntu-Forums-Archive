---
title: "Triple monitor problems"
date: 2011-07-17
forum: General Help
---

### Post by annoyingrob on 2011-07-17
I've had a dual monitor setup for some time now, with an 8800GTS 512 video card, and two 23" 1080p LCD monitors. I was using twinview supplied with the nvidia drivers, and everything worked great.

Fast forward to last week, I got a third monitor (30", 2560x1600 resolution). I set up the 8800GTS running the 30" and one 23" using twinview and it worked fine. I then installed a 2nd graphics card in the machine (8800GTX 640), and connected the 2nd 23" monitor to it. 

As soon as I enable the third monitor as a separate X instance, the twinview gets all messed up. Normally the gnome panels stretch across the 30" just fine, the backgrounds on the two monitors are fine, but as soon as the 2nd x server is started, it treats the other two monitors as a giant 4400x1600 desktop, stretching the panels across both, stretching the desktop image across both, maximizing windows across both, etc. I don't want that. 

Does anyone have any ideas as to why twinview works fine with my two different sized monitors normally, but as soon as I add another x server, it gets dumb, and treats them as one giant box?

---

