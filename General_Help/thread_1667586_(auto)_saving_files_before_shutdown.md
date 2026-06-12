---
title: "(auto) saving files before shutdown"
date: 2011-01-15
forum: General Help
---

### Post by thaitang on 2011-01-15
I am wondering if there is already a feature, and if not, then a way to save any open files before a shutdown occurs?

I use xfce4 battery plugin and there is the option to invoke a shutdown whn the batt. hits critical percentage, but I would like to be able to run something at the low percentage stage to save any open files in case the critical stage is reached. I have had no luck googling any solutions or potential solutions.

Any pointers int he right direction or ideas would be great!

thanks,
tt

---

### Post by ajgreeny on 2011-01-15
How about hibernating instead of shutting down when the battery gets too low.  That way all files would be still open, but saved in the hibernated state, ready to be saved properly when you restart.

---

### Post by thaitang on 2011-01-15
> **ajgreeny said:**
> How about hibernating instead of shutting down when the battery gets too low.  That way all files would be still open, but saved in the hibernated state, ready to be saved properly when you restart.
Thanks for the reply ajgreeny.

This is gonna sound kind of dumb I am sure, the hibernate option has crossed my mind but I have never got hibernate to work for me on my laptop using ubu/xubu; not that I have ever expended much energy looking too far into the issue to try seriously to resolve it. For this particular situation, I just thought there might already be an applet/plug-in/script solution available that auto-saves open files.

cheers,
tt

---

### Post by ajgreeny on 2011-01-16
You need plenty of swap to hibernate, but usually 2GB is enough.  If it still does not work with a 2GB swap size you could try enlarging swap with gparted from the live CD to 4GB, and try again, but there are some hardware combinations that simply refuse to hibernate.

---

