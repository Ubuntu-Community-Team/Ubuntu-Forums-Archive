---
title: "using XVesa X11 server over Xorg"
date: 2009-12-08
forum: General Help
---

### Post by foxofinfinety on 2009-12-08
hello, been a while since I logged on here.
normally use forum.ubuntu-nl.org, since I'm dutch.


I since recently (yesterday...:P) use Xubuntu on my laptop.
which is a medion (lifetec) LT9399 notebookPC.

and it runs, but not great.
and I think it's because of the X11 server.
Xorg is powerful, but heavy, and my laptop is not.
(600Mhz Mobile Intel Pentium 3 and 128MB RAM)
I had Puppy Linux on it for a while and that ran nice and fast, but it didn't run the programs I use.

I looked at the memory usage in Xubuntu and it's about the same as Puppy Linux.
except for one program: Xorg.
Puppy Linux (optionally) uses XVesa.
and with XVesa the laptop is quite fast.

does anyone know if I can replace the Xorg X11 server with XVesa?
and if so, how I can do that.

I use Xubuntu 9.10.
I can compile something if needed, but if there's a .deb.... :biggrin:
if re-installation is needed that's also ok, since I don't have anything on there that's not in the repositories, so I can get it back rather fast (well, you know, linux :D).

---

### Post by inclusivedisjunction on 2009-12-29
To my knowledge, xvesa isn't a separate program, but a compile-time option for XFree86. X.Org was forked from XFree86, but I think they ditched the xvesa-specific portion. You probably won't find any .deb packages of recent versions of XFree86 or xvesa because of the change in licensing, but you should be able to build it yourself from source.

[http://www.xfree86.org/releases/rel480.html](http://www.xfree86.org/releases/rel480.html)

---

