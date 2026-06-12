---
title: "Will upgrading mess my GRUB??"
date: 2006-06-02
forum: General Help
---

### Post by shaynaynay on 2006-06-02
I tried to upgrade from the apt, and then I got all the X server error thing...
It's a good thing that before the restarting I changed the GRUB to point (by default) to my WIN XP.

So, now I've downloaded the final 6.06 CD, and want to install it... now I'm afraid that this will mess up (or "reinstall") GRUB, and I wont be able to log to my windows again. (I mean, without going "fixmbr" thing and lose my linux...).

Is it safe to install?
Sorry for my English.

Thanks,
Guy.

---

### Post by blakamin on 2006-06-02
GRUB should recognise your windows installation straight away... If you partition properly, there should not be a problem (manual partition)

---

### Post by shaynaynay on 2006-06-02
[QUOTE=blakamin]GRUB should recognise your windows installation straight away... If you partition properly, there should not be a problem (manual partition)[/QUOTE]

I'll tell you what..
After reading this [[http://ubuntuforums.org/showthread.php?t=186453]](http://ubuntuforums.org/showthread.php?t=186453]) I'm now totally confused...

I have windows partition, and a linux partition. Both work fine. I'm also using GRUB. After reading the thread I don't know what will happen to my GRUB, MBR and/or partitions...

---

### Post by blakamin on 2006-06-02
you will have the choice (on a live or alternate cd) of letting it automatically resize (killing everything) partitions, or "manual".... choose manual and you'll get options to change mount points, etc...

there is better people to explain that than me....

---

### Post by mattisking on 2006-06-02
You may want to go with the "alternate" installer, one of the ISO's available. I've already read at least one thread with people that used the live cd installation method of grub getting nuked and in some cases, other partitions lost.

---

