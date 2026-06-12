---
title: "Emerald Theme Manager / Compiz Issue"
date: 2009-12-29
forum: General Help
---

### Post by Dahmwern on 2009-12-29
Hey everyone,

Yes, this is my first post.  Caveat's: Yes, I couldn't decide where to put this so I have put it in the general section and I will let a mod move it if it is truly incorrectly placed.  Now on to the good stuff!

What I'm running (so you know):
- Ubuntu 9.10 in VMware Fusion as a Virtual Machine on a MacBook Pro
- Problem occurred in Gnome

I've installed Emerald Theme Manager, and all the Compiz packages that go along with it, etc.  I can open Emerald Theme Manager and it will display all the themes I have, but when I click on one it will not change it.

Research told me to input "emerald --replace" into a run command.  I tried this (through the terminal) and it restarts my system!  When I tried to log back Gnome, it restarted my system again, but then let me log in after that.  

Thinking this was just a fluke, I attempted to make "emerald --replace" a reoccurring run command at start up ---- BAD IDEA.  Now, every time I attempt to log into Gnome, or XFCE, my system restarts itself.  I can still log into Fluxbox though...

Any ideas on why "emerald --replace" is rebooting my Gnome and XFCE, and what I can do to stop "emerald --replace" as a reoccurring run operation?


Thank you, in advance.



EDIT: So, through Fluxbox I get to Synaptic Package Manager and was able to completely remove Emerald, and Emerald Themes.  Fortunately, now I can run GNOME again.  I would still like to know why Emerald Theme Manager was such an epic failure, and why "emerald --replace" did not correctly replace my current window manager, and instead crashed my system...

---

