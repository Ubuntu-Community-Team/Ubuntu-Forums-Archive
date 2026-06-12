---
title: "weird stutter in Ubuntu 8.10"
date: 2009-08-04
forum: General Help
---

### Post by rybu on 2009-08-04
Hi all, 

I've been running Ubuntu 8.10 on my laptop (Thinkpad T61p) since 8.10 has been available.  Things have been going mostly pretty smoothly but it appears as if a recent update has caused some trouble.  I'm having trouble figuring out the cause of the problem though. 

The symptom is that about once every couple of minutes the system will stutter.  For example, if I'm typing, sometimes I'll get a repeat of 8 or 9 keystrokes -- but the key isn't stuck.  Or if I'm playing something in the Adobe Flashplayer, it'll sound like a skipping CD at the same time the computer seems to think the key is being held down (of course the key is not being held down).  It seems the computer is running fine otherwise -- background tasks running as usual.  top doesn't report anything hogging cpu cycles or memory. The mouse cursor becomes "stuck" during the stutters -- but at every lurch it gets updated. 

If it's any help, I'm running the 64 bit version of Ubuntu, with the latest NVIDIA-supplied video drivers. 

I did a little poking around the site but couldn't find a similar (recent) problem. 

And strangely, as I type this the problem has gone away but as far as I can tell nothing has changed in terms of what tasks are running. 

Ideas??

---

### Post by Technoviking on 2009-08-04
I had some problems with NVidia issue in Ubuntu 8.10, upgrading to Ubuntu 9.04. 

T-V

---

### Post by otz070 on 2009-08-04
if your using gnome with the gnome panel, check the panels cpu usage when it does that. I've had it happen alot and that was what was causing mine. (had to restart gnome panel)

(I actually ended up switching to open box in the end)

---

### Post by rybu on 2009-08-05
> **otz070 said:**
> if your using gnome with the gnome panel, check the panels cpu usage when it does that. I've had it happen alot and that was what was causing mine. (had to restart gnome panel)

(I actually ended up switching to open box in the end)

I'm using Gnome but gnome-panel seems to be working fine when these stutters happen.   There's nothing anomalous at all in terms of cpu or memory usage when the stutters happen -- at least according to top.   But thanks for the suggestion.  

It's strange that the stutter started after the last kernel upgrade.  I wasn't having anything like this last week.

---

### Post by rybu on 2009-08-12
It appears to be iwl4965/1. The problem went away for the past week, but today it's back. Moreover, I notice that iwl4965/1 jumped up top's list when it starts, then goes away when the spasms dissappear.

edit: I thought I'd disable wireless but iwl4965/1 continues to cause trouble even with wireless off.

---

