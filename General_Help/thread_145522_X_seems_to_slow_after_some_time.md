---
title: "X seems to slow after some time"
date: 2006-03-16
forum: General Help
---

### Post by krazyjim on 2006-03-16
HI all,
My system seems to get sluggish after around an hour, starts as windows staggering when I move them and goes on to cause things like interruptions in audio playback with Rhythmbox and long delays between starting an application and it actually opening.

From a gDesklets app i have CPU usage and RAM are never 100% so I am tempted to put it down to slow disk access although i have DMA enabled and my disk is on it's own channel possibly caused by limited memory.

Another thing I suspect is my integrated graphics (would explain poor redraw performance).  Has anyone had any experience with these issues or knows anything about how to solve them?

My system specs:
custom compiled kernel v2.6.12 using(precompiled binaries, both 386 and 686 archs produce same result)
Ubuntu 5.10 with latest app updates

Hardware:
Celeron D @ 2.53 GHz
256MB RAM (have run memtest86 on and passes)
Integrated graphics (shares 64MB of system RAM)
40gb Seagate HD
root filesystem is in an LVM group.

---

### Post by Ivan Matveich on 2006-03-16
Try 'swapoff -a' (disable swap devices) and see if that helps.

---

### Post by super on 2006-03-16
i would suggest getting a bit more ram. 256mb - (64mb shared) is not really very much or get a cheap nvidia video card. the accelerated graphics will make a significant difference.

another possible problem is that some programs use memory even after they have been closed. you might want to watch that also.

---

### Post by krazyjim on 2006-03-16
I've just started using KDE (seems more responsive than gnome) and looking at the Information Center I have 3.4MB of RAM left so I think getting a new graphics card will fix it, I have an old geforce 4 somewhere. Thanks for the replies :)

---

