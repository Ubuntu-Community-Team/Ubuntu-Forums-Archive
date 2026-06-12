---
title: "keyboard problem (9.10)"
date: 2010-02-16
forum: General Help
---

### Post by daka on 2010-02-16
I have a Spanish keyboard and when I delete "US" and add Spanish keyboard (so that there is only a Spanish configuration assigned) on the next reboot it initializes the US keyboard again.  Does anyone know how to stop this from happening?

daka

---

### Post by InspiredIndividual on 2010-02-16
Did you click "Apply System Wide" after your changes?

---

### Post by daka on 2010-02-17
Yes, I clicked "Apply System Wide"

daka

---

### Post by InspiredIndividual on 2010-02-17
Mmm, this is a bit strange... I did some searching around. It seems this used to be a bug... which was supposed to be fixed in 8.10 already! You could try to fix it manually. If you need any help or run into difficulties, just ask.

The most concise instructions can be found here: 
[http://ubuntuforums.org/showthread.php?p=5989729#2](http://ubuntuforums.org/showthread.php?p=5989729#2)

You will need the correct language key for your specific keyboard. A list can be found here:
[http://ubuntuforums.org/showthread.php?t=772511&page=2#14](http://ubuntuforums.org/showthread.php?t=772511&page=2#14)

These are similar threads. I don't think you'll need them, but I'll post them for completeness sake.
[http://art.ubuntuforums.org/showthread.php?p=5185453](http://art.ubuntuforums.org/showthread.php?p=5185453)
[http://ubuntuforums.org/showthread.php?t=922351](http://ubuntuforums.org/showthread.php?t=922351)

Let us know if you managed to solve your problem or if you need more help.

---

### Post by rnerwein on 2010-02-17
> **daka said:**
> Yes, I clicked "Apply System Wide"

daka

hi
right mouse klick at your upper panel --> add to panel --> select keyboard indicator

then you can change the keyboard layout on the fly ( i use a german and a thai keyboard )
ciao

---

### Post by daka on 2010-02-17
Thanks guys.... most strange.... I tried the xorg.conf fix, broke my system, undid everything in rescue mode, with vi, and followed rnerwin's advice, putting the keyboard selection on the panel and so far so good, it is staying as Spanish (I don't have any idea why!)... but had a bit of a heart attack there.....at least I discovered that maybe I am graduating out of "newbie" mode poco a poco.

Thanks again for the help!  I suspect maybe that old fix maybe doesn't work for 9.10??

daka

---

### Post by InspiredIndividual on 2010-02-17
Oops, I wasn't aware of any possible problems with the methods I linked to. Sorry about that. Nice to see you managed to solve the problem.

---

### Post by daka on 2010-02-17
NO PROBLEM .... I appreciated the effort.... and I learned some new things.... usually I would just re-install but this time I was able to make a basic recovery in terminal so I was happy!

Cheers

daka

---

