---
title: "MAME performance problem: hitches &amp; stutters"
date: 2010-06-01
forum: General Help
---

### Post by Objekt on 2010-06-01
I don't know if there are a lot of Multiple Arcade Machine Emulator (MAME) gamers on this forum, but I figured I'd give it a shot.

I recently got into MAME, installing the GMAMEUI frontend (version 0.2.11, Sourceforge project page here: [http://gmameui.sourceforge.net/]("http://gmameui.sourceforge.net/")).  The actual executable that runs the games is listed in System Monitor as "sdl-mame" (or "SDLMAME" on the window title).

On to the problem proper: When I'm playing games through GMAMEUI, every so often the game will stutter and/or skip frames in a very disruptive fashion.  Interestingly, it seems to be only a video problem.  Game sounds do not drop out or distort.  But the stuttering can cause the game animation to get so choppy that I can't see what I'm doing.

It happens with all games, so I don't see how it could be a bad ROM.

When the stuttering happens, it's not due to lack of system resources in general.  I had a bunch of stuff running when I first noticed the problem, but was only using a total of 1 GB of RAM out of 4 GB (system specs in my sig).  I observed the problem again just now, with only Firefox, Evince with a .pdf open, and System Monitor running in a window beside the SDLMAME window.  The stuttering happened whenever sdl-mame's CPU use exceeded about 40%.  It mostly sat at 30%-40% but would occasionally spike to 60%, 70%, sometimes even 100%.  At these times, the visual stuttering was obvious.

I've tried setting the sdl-mame process to highest priority (-20 nice value), but [s]this has no effect.[/s] System Monitor crashes.  Weird.

I am also using the realtime Linux kernel (2.6.31-9-rt), which was supposed (I thought) to prevent this sort of thing.  

What's going on here, and how do I fix it?

What is going on here, and how do I fix it?

---

### Post by Gordon D on 2010-12-14
Just installed it myself and have the same problem.

Dual boot m/c with Windows XP. Don't have the same issue with running Mame under XP.

Any ideas?

---

### Post by blackaardvark on 2011-04-27
Just encoutered this problem on my machine. It is really irritating!

---

