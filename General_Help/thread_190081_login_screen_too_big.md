---
title: "login screen too big"
date: 2006-06-05
forum: General Help
---

### Post by rplantz on 2006-06-05
My Ubuntu login screen (where I enter my user name and password) is about 1.5 times larger than my monitor. If I move my mouse to the edge of the monitor, the screen scrolls so that I can eventually see the whole thing.

Once I log in, everything is fine.

This behavior started when I installed Kubuntu. Using Synaptic's history, I completely removed all the packages that got installed with Kubuntu.

I have reinstalled nvidia-glx, nvidia-kernel-common, ubuntu-artwork, and gdm. I don't see anything in the configuration files that would cause this behavior.

Although it's usable, I would like to get my login screen back to it's correct size.

---

### Post by pyromithrandir on 2006-06-05
Open up your xorg.conf, go to the "Screen" section and find the "Display" subsection that has the same "Depth" as the "DefaultDepth" line.
Add a line in that subsection that says 
> Virtual *xdim* *ydim* where *xdim* and *ydim* are the x and y resolution that you want the screen to be. For example, if you want to use 1024x768, make it say > Virtual 1024 768

Right now, what your computer is doing is having a "Virtual" display that is bigger than the screen's actual resolution.

---

### Post by rplantz on 2006-06-05
[QUOTE=pyromithrandir]Open up your xorg.conf, go to the "Screen" section and find the "Display" subsection that has the same "Depth" as the "DefaultDepth" line.
Add a line in that subsection that says 
 where *xdim* and *ydim* are the x and y resolution that you want the screen to be. For example, if you want to use 1024x768, make it say 

Right now, what your computer is doing is having a "Virtual" display that is bigger than the screen's actual resolution.[/QUOTE]

Bingo! Thank you!

---

### Post by sapincher on 2008-04-17
I have the almost the same problem, except that my logon screen window does not move around when my mouse is on the edge. My xorg.conf does have "virtual 1280 800" in exactly the right place, but it doesn't fix the problem. It only happens with the "nvidia" driver. It is usable to a certain extent, but the session and system buttons are cut off along with half of the username entry box. What are other methods of repairing this?

---

### Post by frrossk on 2008-05-07
In xorg.conf, under "Screen" section, the value for "Virtual" (1280 1024, for example), has to be the same as the first value in the Modes line (like "1280x1024@60") (it worked for me)

---

