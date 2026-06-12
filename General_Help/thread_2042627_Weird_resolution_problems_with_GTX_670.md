---
title: "Weird resolution problems with GTX 670"
date: 2012-08-15
forum: General Help
---

### Post by DanB91 on 2012-08-15
I recently installed Ubuntu and have 302.17 drivers for my GTX 670 (the version before the one released a few days ago).  

I use a Westinghouse HDTV as my monitor (hooked up via VGA) which goes up to 1366x768.  For some odd reason, the Nvidia settings will read the monitor I am using as a Westinghouse and allow me to go up to 1366x768.  And then randomly, (sometimes when I launch an application or a new window is drawn to the screen), the resolution will kickback to 1024x768 and read my monitor simply as CRT-0.  I can go into Nvidia-settings and change it to 1360x768, but it cuts off a few pixels and looks a bit stretched on my monitor.

Randomly, under the same circumstances, the graphics card will re-detect my monitor as a Westinghouse and go back to 1366x768.  And it goes back and forth.  I do not have this issue with Windows, so I don't think it's the monitor/HDTV (though I am thinking the linux nvidia driver does have a problem with it).

What I have tried:

-Updated to 304.27 which was released a few days ago.  The same issue occurs and Steam wouldn't launch so I reverted back until maybe the update Wine to have it work.  But I have decided I'll probably just use Windows for games for now (until Steam goes on Linux), so I might update back to 304.27.

-Plugged in via HDMI.  I do not have this issue when I do this, but, for some reason (I am thinking, though I might be wrong, because the monitor/HDTV only expects up to 720p on the HDMI port, not 1366x768 ) the picture looks much worse, so, I went back to VGA.

Any ideas?  Is it just that the proprietary Nvidia Linux driver doesn't like my HDTV?  I'd prefer to keep the proprietary drivers, so I am hoping there is some sort of work around.

Also as a side question: when do they normally update the nvidia-current package with new drivers after they come out?

Thank you very much!

---

### Post by DanB91 on 2012-08-15
Anyone?

---

### Post by DanB91 on 2012-08-15
Bump

---

### Post by Bobhuber on 2012-08-15
> **DanB91 said:**
> Anyone?
Both those drivers are causing me problems in gnome 3.    295.59 should fix your problems.

---

