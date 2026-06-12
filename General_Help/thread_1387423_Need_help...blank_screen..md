---
title: "Need help...blank screen."
date: 2010-01-21
forum: General Help
---

### Post by thermal_dl on 2010-01-21
Hi all.
I'm a ubuntu newbie.  I installed ubuntu today and it ran fine and i tried doing something with compiz and now the screen is completely blank, no mouse curser.
Every time I boot up it is a blank screen after I select ubuntu.
Windows 7 works fine on a seperate partition and also I can get into recovery mode.
I was thinking delete the ubuntu partition and start back over.  How can I do that and is there an easier way to solve this problem? 

It is a brand new Sony i5 core laptop with Nvidia 330M 


thanks

---

### Post by quixote on 2010-01-23
It sounds like the laptop should be able to run compiz okay, but the first thing to try is to turn that off.  When you boot, select "recovery mode", not your usual selection.  That boots into a command line terminal without any graphics.  (You are root, so be very careful not to make any typos!) At the prompt type ```
#metacity --replace
```(Don't type the hash mark.  That's just to represent the prompt.) That will replace compiz with the less memory-intensive metacity.

Then shutdown again by typing ```
#halt now
```

Restart, this time selecting your regular ubuntu, and let's hope for the best! :)

---

