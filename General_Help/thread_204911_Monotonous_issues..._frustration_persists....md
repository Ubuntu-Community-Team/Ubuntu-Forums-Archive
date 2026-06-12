---
title: "Monotonous issues... frustration persists..."
date: 2006-06-27
forum: General Help
---

### Post by Patrick-Ruff on 2006-06-27
Ok well... I've been using Ubuntu for months now, and I've just been wondering why windows still holds benefits over it... (I'm not talking compatability issues entirely). but I mean, Gnome seems to be sluggish graphically, and there doesn't  seem to be anything being done about this.  I mean, problems just persist, there doesn't seem to be many easy solutions.. Windows seems to have a much faster desktop environment, so, why can't Gnome be just as fast as windows' environment?  I mean, I just want an OS that will simply, just work. I don't like to run into crazy *** problems that take hours to solve, I don't have the free time or the patience to do such things..  can anyone give me logical explinations to such things? do NOT tell me to go back to windows, I seriously hate it when poeple do that.

---

### Post by keithjr on 2006-06-27
[QUOTE=Patrick-Ruff]Ok well... I've been using Ubuntu for months now, and I've just been wondering why windows still holds benefits over it... (I'm not talking compatability issues entirely). but I mean, Gnome seems to be sluggish graphically, and there doesn't  seem to be anything being done about this.  I mean, problems just persist, there doesn't seem to be many easy solutions.. Windows seems to have a much faster desktop environment, so, why can't Gnome be just as fast as windows' environment?  I mean, I just want an OS that will simply, just work. I don't like to run into crazy *** problems that take hours to solve, I don't have the free time or the patience to do such things..  can anyone give me logical explinations to such things? do NOT tell me to go back to windows, I seriously hate it when poeple do that.[/QUOTE]


Where does Gnome seem sluggish?  And have you installed your video card's linux drivers?  Gnome has always been quick for me, and less bloated than windows.  

You don't mention many specifics.  This might not be the forum of choice for such a thread.

---

### Post by Patrick-Ruff on 2006-06-27
yeah, appologies for the lack of specifics. I mean, gnome doesn't pre-load icons and other desktop environment stuff into memory before the desktop environment loads. and I have installed my video card linux drivers and they're working properly  I think the main thing for lack of speed is the fact that its very hard drive dependant, it doesn't load stuff like that into memory from the get go. also, pre-link and preload never worked well for that..

---

### Post by 23meg on 2006-06-27
> so, why can't Gnome be just as fast as windows' environment?Basically because the Windows GUI utilizes hardware acceleration better than X at present.

---

### Post by Patrick-Ruff on 2006-06-27
will this improove in the future? like near future...

---

### Post by nanotube on 2006-06-27
i suspect that maybe you just have too little ram for gnome to run fast. i have 768 megs, and gnome just flies. how much ram do you have on your box? if you have 256M or less, you would get much better performance out of XFCE (install package xubuntu-desktop, and choose XFCE that at login from your list of sessions). Gnome isn't made for low-ram systems.

---

### Post by Patrick-Ruff on 2006-06-27
I have 512, the video ram is on-board. not shared.

---

### Post by Patrick-Ruff on 2006-06-27
also, I noticed such sluggie-ness with my desktop, its very fast to. 2.8Ghz P4 HT, 786MB of ram, nVidia GeForce 6600GT PCI Express.

---

### Post by 23meg on 2006-06-27
[QUOTE=Patrick-Ruff]will this improove in the future? like near future...[/QUOTE]
With AIGLX getting full driver support and integration into X such problems will be history.

---

### Post by 23meg on 2006-06-27
[QUOTE=Patrick-Ruff]also, I noticed such sluggie-ness with my desktop, its very fast to. 2.8Ghz P4 HT, 786MB of ram, nVidia GeForce 6600GT PCI Express.[/QUOTE]X will almost always be slower than the Windows GUI in 2D drawing operations such as redraws, antialiased font rendering, window resizing etc. given the present state of things. 

You started many other threads with the same complaint; you can resort to my advice in them to make things just about as fast as can be. If you still find things slow, you'll either have to live with the slowness, or quit using X.

---

### Post by Patrick-Ruff on 2006-06-27
I'de prefer not quit, so I wont see any major performance increases till Edgy? also, will AIGLX have the wobbly windows and little open gl effects like that?

---

### Post by 23meg on 2006-06-27
[QUOTE=Patrick-Ruff]I'de prefer not quit, so I wont see any major performance increases till Edgy? [/QUOTE]Probably not with Edgy either. just make sure your video hardware is utilized correctly, and again, take a look at what I suggested before. You didn't respond to me when I asked you whether powernowd (which might be slowing down your processor without any benefit) was running on your system last time.
> also, will AIGLX have the wobbly windows and little open gl effects like that?Not necessarily; only if you enable them. You'll be able to have your normal 2D desktop like you have with a default Dapper install, and it will be as snappy as Windows, if not better.

---

### Post by Patrick-Ruff on 2006-06-27
interesting, is it possible to install aiglx on ubuntu now? also, I disabled powernowd before, it did not increase performance in any way.

---

### Post by 23meg on 2006-06-27
[QUOTE=Patrick-Ruff]interesting, is it possible to install aiglx on ubuntu now? [/QUOTE]Yes, except on Nvidia hardware. 

> also, I disabled powernowd before, it did not increase performance in any way.Just make sure your CPU is running at full speed after you kill powernowd, since it's what powers most drawing operations.

And please don't start another thread with the same issue; if you have more questions, post them in one of the threads you already started (the previous one was more descriptively titled).

---

### Post by Patrick-Ruff on 2006-06-27
ok, what did you mean except on nvidia hardware? it will only work with ATI? if so, that will accomidate my needs greatly, since my laptop is running an ATI card, how would one install aiglx? and the CPU was running at full speed.

---

### Post by 23meg on 2006-06-27
AFAIK it works with most ATI and Intel hardware right now. Do a forum search for AIGLX and you'll find the guide(s) you need.

---

### Post by Jasper Houtman on 2006-06-27
Both Nvidia and ATI are both still very poorly supported I'm afraid.
Might be a while till this is solved.

---

### Post by Patrick-Ruff on 2006-06-27
well, this seems to be a rendering issue. or a lack of loading icons and such into memory...ether way... it should be solve-able.

---

### Post by keithjr on 2006-06-27
On another note, do you use swap space?  This could dramatically improve performance.

---

### Post by nanotube on 2006-06-27
[QUOTE=23meg]X will almost always be slower than the Windows GUI in 2D drawing operations such as redraws, antialiased font rendering, window resizing etc. given the present state of things. 
[/QUOTE]
well, i beg to differ. my laptop (3ghz p4, 768mb ram) dual boots win xp and ubuntu dapper, and i can't say that dapper is any less snappy than xp, on this same machine. windows move and minimize instantaneously, menus pop up immediately, and all that good stuff.

in fact, if anything, ubuntu is /better/ at multitasking - under xp (back in the old days, i haven't actually /used/ xp ever since i installed breezy :) ), when running too many things at the same time, stuff would get paged to disk, and it would take a long time to get it back up. ubuntu seems to do some magic that severely minimizes the usage of the disk swap, and thus is much more responsive under heavy multitasking. 

so, my guess is that it is some kind of misconfiguration on your comp...

---

### Post by 23meg on 2006-06-28
What I'm talking about is acceleration of 2D drawing operations via the GPU, which is underutilized in X. This can be remedied with a fast CPU, but it's still not an optimal solution, since the CPU spends cycles doing jobs that the GPU should be doing, while the GPU sits idle.
[QUOTE=nanotube]in fact, if anything, ubuntu is /better/ at multitasking - under xp (back in the old days, i haven't actually /used/ xp ever since i installed breezy ), when running too many things at the same time, stuff would get paged to disk, and it would take a long time to get it back up. ubuntu seems to do some magic that severely minimizes the usage of the disk swap, and thus is much more responsive under heavy multitasking.[/QUOTE]
Ubuntu *is* better at multitasking, but that has nothing to do with what I'm talking about. Thanks to the excellent memory management of the Linux kernel Linux distros carry multitasking load much better than Windows, generally speaking. Under heavy load from multiple applications (whose equivalent would make a Windows system choke) the system is still very responsive, but this is a kernel memory management and I/O scheduling matter, not a 2D graphics one.

---

### Post by 3rdalbum on 2006-06-28
It must be some kind of misconfiguration. I have an entry-level machine with 256meg, and Ubuntu flies even when X is running on vesa mode. Much, much faster than Windows.

---

