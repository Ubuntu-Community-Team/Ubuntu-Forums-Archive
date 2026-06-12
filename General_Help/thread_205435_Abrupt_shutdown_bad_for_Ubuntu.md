---
title: "Abrupt shutdown bad for Ubuntu?"
date: 2006-06-28
forum: General Help
---

### Post by Etoile on 2006-06-28
If you shut down Windows "'incorrectly" it breaks stuff.  I guess this is how the drive gets fragmented and all that.  Suffice to say that Windows wants to be shut down properly, using the Shut Down button, etc.  (I remember when you used to have to wait until it said "It is safe to turn off your computer" before you could actually shut down!)

Is this a concern with Ubuntu?  Obviously the preferred thing to do is shut down properly, and I've watched the shutdown process so I know it does some important stuff, but what happens if it gets shut down accidentally? (I've kicked the power cord out under my desk at work more times than I care to admit!)  Will Ubuntu be okay if it just shuts down abruptly?

---

### Post by kripkenstein on 2006-06-28
Well, I would say that it depends mostly on the filesystem that you use, and less on Ubuntu itself. Both ext3 and reiserFS are, in theory, able to recover from abrupt shutdowns with minor if any damage. At least that has been my experience with them.

But, yes, proper shutdowns are the way to go... :)

---

### Post by Al3xanR0 on 2006-06-28
[QUOTE=Etoile]If you shut down Windows "'incorrectly" it breaks stuff.  I guess this is how the drive gets fragmented and all that.  Suffice to say that Windows wants to be shut down properly, using the Shut Down button, etc.  (I remember when you used to have to wait until it said "It is safe to turn off your computer" before you could actually shut down!)

Is this a concern with Ubuntu?  Obviously the preferred thing to do is shut down properly, and I've watched the shutdown process so I know it does some important stuff, but what happens if it gets shut down accidentally? (I've kicked the power cord out under my desk at work more times than I care to admit!)  Will Ubuntu be okay if it just shuts down abruptly?[/QUOTE]

You want to perform a proper shutdown for obvious reasons (slight chance of breakage), however, what is the difference between an abrupt shutdown an a power failure? That is what EXT3 journaling capability is for, to minimize the breakage in the case of improper/abrupt shutdown. I you need to shut down that fast try ```
sudo halt
``` or ```
sudo shutdown now -h
```

---

### Post by Etoile on 2006-06-28
I guess rather than abrupt I should have said unexpected.  It's not that I need to shut down more quickly than it normally goes, it's more that I worry about things like power failure.  Thanks!

---

### Post by mbeierl on 2006-06-28
The thing that I find extremely funny (not that powerfails are funny) in all this is back in the days of ext2, NTFS proponents would slam linux for the lack of a journalling file system.  The broad generalization was that ntfs was much safer.  :roll: 

That being the case, why then does MS Windows expect users to shut down properly? There shouldn't be any need for chkdsk to run in that case, wouldn't there? :-\" 

I mean, sure there could be apps running that could corrupt their own data, but outside of that, if I shut all apps down, technically I should be good to hard power down at that point.

But I must say that in all of my Ubuntu playing (say for hibernation) I've essentially hard terminated my OS well over 30 times without a single instance of corruption.

Others mileage may vary...

---

### Post by Ocxic on 2006-06-28
the same goes for me, one of my harddrives is in bad shape, and everynow and then locks up me comp, and i hard power down, havn't had a problem yet, tho i pray to the computre Gods every time i do it. I'm using XFS by the way.

---

### Post by _simon_ on 2006-06-28
I use ext3 and my install has booted fine from 2 power outages.

---

