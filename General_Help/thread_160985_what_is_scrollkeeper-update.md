---
title: "what is scrollkeeper-update?"
date: 2006-04-16
forum: General Help
---

### Post by nanotube on 2006-04-16
booted my comp today, and saw this proccess called "scrollkeeper-update" eating some cpu. it worked at it for a few minutes then went away. but left me wondering what it is. 

searching on google turned up the man page, that rather unhelpfully says
> This synchronizes the scrollkeeper database with the OMF directory. It searches the scrollkeeper OMF directory to identify if any files were added, removed, or modified and updates its internal database files to reflect any changes.

not knowing what the omf directory is, and what the scrollkeeper database is supposed to be, that tells me nothing.

so, can anyone shed light on this mysterious process? :)

---

### Post by croak77 on 2006-04-16
"Scrollkeeper is cataloging system for documentation on open systems."

[http://scrollkeeper.sourceforge.net/](http://scrollkeeper.sourceforge.net/)

---

### Post by nanotube on 2006-04-16
thanks!
i guess if i had only searched for scrollkeeper rather than scrollkeeper-update, i would have found it. :)

---

### Post by humina on 2006-08-21
Is this process necessary?  It eats up my cpu cycles at inopportune times (like when my laptop is running on its battery).  How do I disable this process?

---

### Post by _simon_ on 2006-12-31
For the first time today I've had an issue with this.

I noticed a huge continous CPU usage spike, on looking at All Processes, scrollkeeper-update was using 90+% cpu. I had to kill it to be able to continue what I was doing.

Is scrollkeeper needed and how would I disable it?

---

### Post by siman on 2007-04-09
today was the first time I noticed scrollkeeper-update. I understand it updates a DB with metadata... but what for? Can some one who knows elaborate?

---

### Post by Psy-Q on 2007-05-27
I would like to get rid of it too. Apparently, it indexes the GNOME-related documentation so it should only kick in when a GNOME-related application is installed, but I'd still prefer not to have *any* indexing going on on my system.

Indexing is a pain for laptops on the go :(

Apparently, some people solve this by renaming scrollkeeper-update and making a symlink from scrollkeeper-update to /bin/true. While a hack, if GNOME or Ubuntu provide no way of disabling scrollkeeper officially, it might be our only choice.

I've seen several people complain (in very clear words) about scrollkeeper-update ruining their gaming performance by intermittently hogging the CPU, eating laptop battery etc. If there *has* to be an indexing engine for the GNOME docs, couldn't it at least run with a very low-priority nice level to prevent such problems? Or only during idle time like the Beagle indexing system does? Cwazy!

---

### Post by fela on 2008-03-16
I have this problem too. I think it's ridiculous, if they have to install scrollkeeper on your system, can they at least make it a preference to turn it off? or, like Psy-Q said, make it low priority? scrollkeeper seems even worse than Spotlight indexing on Mac OS X. (except I can't really say as my OS X box has 2x2GHz PowerPC G5 but my Ubuntu box has 1x1.8GHz P4 :S)

I hope Ubuntu/GNOME devs fix this in Hardy/Gnome 2.22. It's pretty much the only really bad thing I've found in Ubuntu yet (and that's saying something, as I've been using it for about 8 months now). It made me think that update-manager had hung, until I looked at system monitor. :confused:

---

