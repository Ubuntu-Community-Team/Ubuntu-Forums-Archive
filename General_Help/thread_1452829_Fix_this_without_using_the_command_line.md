---
title: "Fix this without using the command line?"
date: 2010-04-12
forum: General Help
---

### Post by MASTER260 on 2010-04-12
Hi, I'm MASTER260!  I'm new here, so I might as well introduce myself.  I've used many Ubuntu derivatives I've worked on, except not Ubuntu itself since the 9.04 days.  (I remember using XPGnome in that one.)
 
...Anyways, back to the question.  I'm working on a derivative of Longhorn Linux M2 Beta 2, (which itself is a derivative of Ubuntu 9.10,) &, when I accidentally broke the package system, this appears to be the error that would show up in Synaptic:
 
[http://ubuntuforums.org/showthread.php?t=540286](http://ubuntuforums.org/showthread.php?t=540286)
 
Unfortunately, the solution there is via command-line functions, of which I can't use.
 
The reason lies in the OS I'm developing's base, LH Linux M2 B2.  In the Longhorn Linux M2 Series, the ability to use the Terminal was replaced with a fake Blue Screen of Death in which all it would do is restart the system, as a joke.  The ability to use sh files was supposed to have still worked, but apparently not.
 
Anything I can do?
 
Thanks,
M260

---

### Post by wojox on 2010-04-12
Alt+F2 then gksudo nautilus ?????

Seriously, you replaced the terminal with the BSOD?

---

### Post by MASTER260 on 2010-04-12
> **wojox said:**
> Alt+F2 then gksudo nautilus ?????
 
Seriously, you replaced the terminal with the BSOD?
 I didn't.  Although I am also a Longhorn Linux developer, (in contrast to being the head of the OS I'm basing off of it,) other dev(s) did.
 
And thanks, I'll try when I get home.  (Which won't be for, like, the rest of the day.)  In the meantime, I can use other suggestions, (if their are any,) just in case.  Maybe testing cold be good.  But I obviously don't wanaa force.

---

### Post by MASTER260 on 2010-04-13
All, "gksudo nautilus" seems to do is open Nautilus as root...

---

### Post by philinux on 2010-04-13
Not sure if this will work.

ctrl+alt+f1 would get tty1

then ctrl+alt+f7 to get back to desktop which is tty7

---

### Post by MASTER260 on 2010-04-14
> **philinux said:**
> Not sure if this will work.
 
ctrl+alt+f1 would get tty1
 
then ctrl+alt+f7 to get back to desktop which is tty7
Thanks,I think I'll try that as Plan B.
 
Plan A will be this, with just opening the, "sources," file in gedit, from gedit, rather than opening it in gedit, from the Terminal:
 
[http://itechlog.com/linux/2008/12/18/fix-broken-package-ubuntu/](http://itechlog.com/linux/2008/12/18/fix-broken-package-ubuntu/)

---

### Post by MASTER260 on 2010-04-14
Great news!  Plan A worked!  :KS  NOTE:  For anyone with problem of a corrupt package breaking their whole package system, the, "status," file needs to be opened as root unless you want to save it via overwriting it with a new file.

---

