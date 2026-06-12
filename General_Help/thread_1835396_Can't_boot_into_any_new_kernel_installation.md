---
title: "Can't boot into any new kernel installation"
date: 2011-08-29
forum: General Help
---

### Post by jwingy on 2011-08-29
Hey guys,

I've been having some issues which all started with a sudden sluggish feeling I got doing anything with the GUI.  Most notable is running 3d games in wine, where they used to be smooth, are now stuttering.  I tried different nvidia drivers, but the result was still the same.  Eventually I stumbled upon a long forum post about this, and their conclusion was to install a newer kernel version.

I ended up doing this with the 3.0.3 kernel, and was able to boot into it, but was unable to get wireless or my mouse to work.  I decided I'd try something earlier, but still later than my current kernel 2.6.38.11.  I believe I tried 3.0.1 but was unable to boot into that.  I subsequently uninstalled and reinstalled the 3.0.3 kernel but can't boot into that either.  

Has anyone had this problem before?  Which logs should I be paying attention to?


***UPDATE***

I ended up being able to boot into the other kernels by deleting my xorg.conf, but this or some other change I might've made that I can't remember now ended up mucking up the KDE login (for every kernel) so that everytime I'd attempt to login, it load for a second before dumping me back into the login screen.  I looked around for a fix for that problem but after a few tries at fixing it, I decided the easiest solution at that point was to just restore my system to an earlier image I had made.

---

