---
title: "runlevel 3"
date: 2010-01-13
forum: General Help
---

### Post by Chappy01 on 2010-01-13
Can someone please advise how to start in runlevel 3 with grub 2?

Thanks

---

### Post by john newbuntu on 2010-01-13
After booting in, you could do a Ctrl+Alt+F2 and do "sudo init 3" without quotes.

Otherwise, you would have to edit the Grub2 command menu and boot it at runlevel 3.  Follow the first 7 or 8 slides until you get to the "ro quiet splash" stage and then add a 3 at the end.  Hit enter and "B" to boot
[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

Well, RL 2, 3, 4, 5 all look same to me unless you have performed some tweaks.

---

### Post by Chappy01 on 2010-01-13
Thanks, but what I want to achieve is booting without starting X, my x config is corrupt, and once booted I cannot shut x down to edit the config. All I get is a message "can't open display", need to not start x in the first place.

Thanks

---

### Post by x33a on 2010-01-13
you aren't able to press ctrl-alt-f1 (f2,f3,etc)?

as for starting a particular runlevel, in the legacy grub you just had to append the runlevel number to the parameters in the grub menu. try as john said.

---

### Post by mcduck on 2010-01-13
Your problem here is that Ubuntu (like Debian) doesn't really use such a runlevel..

For Ubuntu/Debian runlevel 1 is single-user mode and runlevel 2 is full multiuser with graphical desktop. Runlevels 3–5 are exactly the same as 2.

Besides, Ubuntu s already moving towards using Upstart which pretty much puts an end to the whole runlevel business.

If you want to boot into text mode you need to disable GDM/KDM (depending on which one you use) from starting.

---

