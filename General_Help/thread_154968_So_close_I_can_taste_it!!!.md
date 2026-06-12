---
title: "So close I can taste it!!!"
date: 2006-04-04
forum: General Help
---

### Post by daveinthecave@gmail.com on 2006-04-04
Hi I have just got my hands on a copy of ubuntu 5.10, it installs fine till after it restarts and loads ubuntu and just before it loads to the os it displays a _ in the top right of the screen and stops.

I was thinking it could be some of my hardware so I removed all the excess drives and cards. and then I tried agian but it stills just stalls.

I have an old pc (intel P2 633 Mhz with 128 Mb of Ram, It was free) so I wondering if is just too old to run.

---

### Post by ESPOiG on 2006-04-04
culd be, but dunno y anyway try ubuntulite i think that is wat it is called... it is for older pc's

i dunno the link for it try google :P

---

### Post by frup on 2006-04-04
does it get in to the grub boot loader? 
what happens before it goes to _

at my house we have one of our ubuntu systems running on a 700mhz duron with 128mb ram and that works.

---

### Post by Darkriser on 2006-04-04
memory might be your problem. consider installing Xubuntu: [https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)

i'm running it on a notebook (300MHz and 172 MB RAM) and it's pretty fast...:D

---

### Post by justleen on 2006-04-04
[QUOTE=daveinthecave@gmail.com]Hi I have just got my hands on a copy of ubuntu 5.10, it installs fine till after it restarts and loads ubuntu and just before it loads to the os it displays a _ in the top right of the screen and stops.

I was thinking it could be some of my hardware so I removed all the excess drives and cards. and then I tried agian but it stills just stalls.

I have an old pc (intel P2 633 Mhz with 128 Mb of Ram, It was free) so I wondering if is just too old to run.[/QUOTE]

you could try this guide [https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems) 

starts out with a server install (eg, bare install) and then add X to it..

---

### Post by daveinthecave@gmail.com on 2006-04-12
Ok i have had another go at installing linux ("ubuntu lite this time") <busy times>  to no avail

just doesnt work at all "unless i stop it" from loading

and hangs my ME on load and will also some time stop at grub and say error 18 and i have tried what other ppl have said about that and it dosent work

any more ideas ne 1?

cheers from the cave.

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=daveinthecave@gmail.com]Ok i have had another go at installing linux ("ubuntu lite this time") <busy times>  to no avail

just doesnt work at all "unless i stop it" from loading

and hangs my ME on load and will also some time stop at grub and say error 18 and i have tried what other ppl have said about that and it dosent work

any more ideas ne 1?

cheers from the cave.[/QUOTE]
Did you use the iso ? Because it doesn't work. Install the base system and then edit your sources.list and then run a sudo apt-get update and then install it.

---

