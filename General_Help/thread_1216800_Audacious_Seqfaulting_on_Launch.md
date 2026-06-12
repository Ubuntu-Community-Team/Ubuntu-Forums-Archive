---
title: "Audacious Seqfaulting on Launch"
date: 2009-07-18
forum: General Help
---

### Post by zigx on 2009-07-18
Hi Guys,

I was wondering if anyone had pointers for how i can figure out what's going on here...

When i try to launch Audacious i get a segfault:
Jul 18 14:51:14 pumped kernel: [ 9011.544274] audacious[11070]: segfault at 0 ip 0000000000441778 sp 00007fff6de4cbf0 error 6 in audacious[400000+e4000]

I've tried removing it and reinstalling and no luck -- any ideas?

thanks.

---

### Post by The Tronyx on 2009-07-18
Hello, is it generating a coredump (core.(0-9)) type file on the system?

Additionally, please provide us with the exact command you are using to launch audacious.  Thanks.

---

### Post by zigx on 2009-07-18
Where can i look for the core dump?

Exact command is: audacious %U 
Also tried: audacious 

Same problem.


Additionally i ran from the command line and see that it might be related to a plugin?  Is it possible to simply remove plugins or something like that?

```
rio@pumped:~$ audacious
/home/rio/.themes/Dust/gtk-2.0/gtkrc:80: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/rio/.themes/Dust/gtk-2.0/gtkrc:81: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/rio/.themes/Dust/gtk-2.0/gtkrc:96: Murrine configuration option "style" is not supported and will be ignored.
/home/rio/.themes/Dust/gtk-2.0/gtkrc:226: Murrine configuration option "style" is not supported and will be ignored.
/home/rio/.themes/Dust/gtk-2.0/gtkrc:335: Murrine configuration option "style" is not supported and will be ignored.
/home/rio/.themes/Dust/gtk-2.0/gtkrc:369: Murrine configuration option "style" is not supported and will be ignored.
amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
Segmentation fault


```

---

### Post by zigx on 2009-07-18
OK so i "Fixed" this by deleting

~/.config/audacious/config 

well, technically, i renamed ~/.config/audacious/config to ~/.config/audacious/config.old

NO IDEA why this fixed it... but it did lol.

---

