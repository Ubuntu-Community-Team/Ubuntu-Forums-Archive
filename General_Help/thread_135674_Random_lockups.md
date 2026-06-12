---
title: "Random lockups"
date: 2006-02-24
forum: General Help
---

### Post by Therrol on 2006-02-24
Ok, I am sort of annoyed. This is my parents first linux experience and I am trying to make linux seem a viable alternative to windows. I installed ubuntu breezy on their computer and showed my dad how to set things up in autmatix and synaptic. So far he has not installed anything.

but my main problem is that ubuntu randomly locks up! I can't even go into a virtual terminal. The only option is to reset. I'm pretty sure the user is allways in firefoc when it does this. The last message I get is this:

Resolved Address "xml:readwrite:/home/therrol/.gconf" to a writable configuration source at position 0

There is a few like that going on for a minute or two. Now, above that there is some bluetooth stuff, but I hjave no bluetooth. It says stuff like Bluetooth: RFCOM TTY layer initalized, but I think this is part of bootup.

---

### Post by encompass on 2006-02-24
It could be a memory problem... windows can run with bad memory for a while.  But linux can be a little touch about it.... so I would do a 'memtest86' from the grub menu.  if you don't have the option there to do the memtest I would put you ubuntu cd in and check it from there.  Had that problem with a system I used a year ago... found it had bad memory and got it fixed; now it runs great.

---

### Post by Therrol on 2006-02-25
nope, passed memtest fine.

---

### Post by Trab on 2006-02-25
have you tried reinstalling ubuntu?
like, from the root?
(BTW for ur parents machine, i would reccomend /home as a seperate partion, makes it easier on them when they have to competely reinstall from CD...)
sometimes ive had ubuntu not install right, things will start...then go to hell...
a reinstall solves even my worst (software) problems (now if i could just remember to power down the system before pluging in new HDDs and RAM... ;-))

---

### Post by lamego on 2006-02-25
Forget about reinstalling, if you didn't something "offensive" like manually installing the wrong driver, reinstalling will get you the system as it is now. 
A few times the lockups on X are caused by the graphical driver, check if ubuntu as selected the best driver for your board or use VESA just to discard the hangup is not related to the video driver...

---

### Post by Jason_25 on 2006-02-25
Is it an AMD processor?  If so, you can try removing the powernowd package.  It has caused alot of people (including me) lockups.

---

