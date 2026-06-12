---
title: "Udpate Glib???"
date: 2006-06-04
forum: General Help
---

### Post by fiba on 2006-06-04
Hi.

ok. i have a little probleme on Ubuntu Dapper.

I try to compile a programme (xchat 2.4.2) and when i type ./configure, He say me that the Glib version must be <= 2.0.3

so.. i look with synaptic my version of glib... it's the 2.0.0                  (2.10.2)

hmm ok i look on the net, and the last version of Glib is 2.11...

How i can update the glib version without (if possible :D) destroy all my ubuntu?


thank's!!

ps: my source.lst is created by the generator (i find on the net...)

thank's!

---

### Post by s6dalane on 2006-06-04
Why not install XChat 2.6.1 from Synaptic?

---

### Post by fiba on 2006-06-04
[QUOTE=s6dalane]Why not install XChat 2.6.1 from Synaptic?[/QUOTE]

yeah i know.... but it's juste for an example.. (xchat or an other programme.. glib will still not be up to date )...

---

### Post by jamiemcc on 2006-06-04
[QUOTE=fiba]Hi.

ok. i have a little probleme on Ubuntu Dapper.

I try to compile a programme (xchat 2.4.2) and when i type ./configure, He say me that the Glib version must be <= 2.0.3

so.. i look with synaptic my version of glib... it's the 2.0.0                  (2.10.2)

thank's![/QUOTE]

You need the corresponding dev packages (libglib2.0-dev) for all required packages.

FYI, the configure checks look for .PC files (in /usr/lib/pkgconfig) to setermine installed version but these are only installed in the dev packages.

---

