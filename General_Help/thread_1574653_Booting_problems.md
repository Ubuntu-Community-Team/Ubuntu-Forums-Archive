---
title: "Booting problems"
date: 2010-09-14
forum: General Help
---

### Post by Leshinsky on 2010-09-14
Ok so somehow out of the blue ubuntu has stopped booting.  When i do the recovery mode it says that there is a fail on some test (a bunch of them) im thinking if i reload the files used to boot the system it will work.  that a file or so got corrupted.  i am duel booting windows and ubuntu.  is there a way to fix this that anyone knows so i dont lose my information in ubuntu.

---

### Post by Lateralis on 2010-09-14
Could you possibly be a little more descriptive about the actual problem and errors you encounter?  For instance, do you see the GRUB boot menu?  If so, can you select to load up Ubuntu and Windows, and does the Windows option work?  what do you see on the screen when you select to boot into Ubuntu?  Does it look like it might be booting and then produce a load of errors?  What do (some of) those errors say?

---

### Post by Leshinsky on 2010-09-14
if i load it normally i will get the curser at the upper left hand corner of the screen and it will not go away.  When i load recovery mode i get a whole list of stuff that failed to load.  but the list moves so fast i cant read it long enough to write it down.  Windows 7 is currently working just fine, which is weird because i loaded ubuntu because for some reason windows 7 would crash every other day and i had to reload it and was getting tired of doing that.

---

### Post by Lateralis on 2010-09-14
So the errors that you get whizzing past, do they ever stop?  Do you get dropped to a recovery shell?  Does the system just stop at some point without dropping to a recovery shell and appear to freeze/crash?  Do you get a "ureadahead" exit status message?  

Have you done any updates recently?  Have you tried selecting a different kernel (You should have a few different kernels listed in the GRUB menu)?

---

