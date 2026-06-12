---
title: "Keeping source - and where?"
date: 2006-01-29
forum: General Help
---

### Post by Rellik on 2006-01-29
Maybe this should go in the "Absolute Beginner's Talk", but I'm not sure, so here it is:

After installing something you downloaded (not via Synaptic or apt-get but just the normal way, i.e. untar + ./configure + make + sudo make install), you need to keep the source (especially the Makefile) around, if you ever want to do an install, correct?  Is there any "standard" place where you're supposed to store the untar'd folder that contains the source?  Would that be /usr/src/, actually?  Not much is in there, so I'm not sure if that's correct.

Thanks :)

---

### Post by dcstar on 2006-01-29
[QUOTE=Rellik]Maybe this should go in the "Absolute Beginner's Talk", but I'm not sure, so here it is:

After installing something you downloaded (not via Synaptic or apt-get but just the normal way, i.e. untar + ./configure + make + sudo make install), you need to keep the source (especially the Makefile) around, if you ever want to do an install, correct?  Is there any "standard" place where you're supposed to store the untar'd folder that contains the source?  Would that be /usr/src/, actually?  Not much is in there, so I'm not sure if that's correct.

Thanks :)[/QUOTE]
Where ever you like, the compiled program is the only thing that needs to be in any special place.

---

### Post by Rellik on 2006-01-29
Thanks!

So /usr/src would be ok then?  That sounds like a good place to me :D

---

### Post by hw-tph on 2006-01-30
I prefer /usr/local/src for software that isn't a part of the distribution.


Håkan

---

### Post by az on 2006-01-30
[QUOTE=Rellik]Maybe this should go in the "Absolute Beginner's Talk", but I'm not sure, so here it is:

After installing something you downloaded (not via Synaptic or apt-get but just the normal way, i.e. untar + ./configure + make + sudo make install), you need to keep the source (especially the Makefile) around, if you ever want to do an install, correct?  Is there any "standard" place where you're supposed to store the untar'd folder that contains the source?  Would that be /usr/src/, actually?  Not much is in there, so I'm not sure if that's correct.

Thanks :)[/QUOTE]
You can use checkinstall to install the built application.  You can then get rid of the source and use checkinstall to uninstall it.  You can also tell checkinstall to turn it into a rudementary deb package so that you can uninstall it using synaptic or another apt frontend.

---

