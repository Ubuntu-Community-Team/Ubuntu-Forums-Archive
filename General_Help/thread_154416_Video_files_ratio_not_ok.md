---
title: "Video files ratio not ok"
date: 2006-04-03
forum: General Help
---

### Post by relix on 2006-04-03
Hi,

I used Automatixx to install non-free drivers for dvd, divx, and what-not. I'm not sure if this has to do with it, but my problem is that every time I play a movie file (any movie file, any player), it has the wrong ratio (it's all too wide and stuff). I can't get it fixed by selecting a differint ratio, although it does change. It's a real bummer and I hate to reboot to Windows just so I can view a video.

Can anyone help?

---

### Post by relix on 2006-04-05
I think I found why it's doing what it does: I have a dual-monitor setup with xinerama (implicitly through the proprietary ati drivers using dtop=horizontal option), so it acts as if I have one 5/4 screen with 2540x1024 pixels, and thus doubles the pixels of the video horizontally. I still don't know how to correct it though, is it a setting in xorg.conf?

---

### Post by relix on 2006-04-05
Silly me, I had the page in my favorites (from when I tried to make my dual screens work (turned out my dual screens don't work in Dapper :( )) with the solution to it:

[http://yolinux.com/TUTORIALS/LinuxAndDualMonitors.html](http://yolinux.com/TUTORIALS/LinuxAndDualMonitors.html)

---

