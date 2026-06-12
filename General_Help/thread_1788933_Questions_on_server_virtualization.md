---
title: "Questions on server virtualization"
date: 2011-06-23
forum: General Help
---

### Post by malfist on 2011-06-23
I have an old low power laptop that I want to repurpose from a paperweight to something useful.
I want to do several things with it, I want to set it up as a subversion repository for my personal code projects, I also want to set it up as a webserver, possibly also as a seedbox, and as a media center.

Because these tasks are rather diverse, I think I'm going to need to setup virtualization. Is this reasonable? What would be the best way to do it? Is VirtualBox capable of running more than one VM at a time, and being administrated from the command line?

---

### Post by haqking on 2011-06-23
> **malfist said:**
> I have an old low power laptop that I want to repurpose from a paperweight to something useful.
I want to do several things with it, I want to set it up as a subversion repository for my personal code projects, I also want to set it up as a webserver, possibly also as a seedbox, and as a media center.

Because these tasks are rather diverse, I think I'm going to need to setup virtualization. Is this reasonable? What would be the best way to do it? Is VirtualBox capable of running more than one VM at a time, and being administrated from the command line?


Well the thing is you say its a low powered machine, how low power ?

and if it is low power, you dont want to be installing an OS, then Vitrualisation software on it, as well as the guest VM running media centre services, subversion etc

or you mean rather than use that laptop, use VM instead ?

andf Virtual BOX is extemely capable....i run a 4gb ram host system and have no problems running 3 or 4 VM's at the same time (vista, XP, Backtrack etc etc) not that happens very often of course.

but i can certainly run 2 or 3 and spin them all on my desktop cube ;-)

IMO virtual box is much better than VMWare, so much less resource intensive i have found anyways

---

### Post by malfist on 2011-06-23
It's low power as in, doesn't consume much power. It still has a fair amount of processing capabilities. It's a 1.5 GHz dual core, the limiting factor is probably going to be hard drive space, which I can upgrade.

---

### Post by snowpine on 2011-06-23
Sounds like a reasonable project, here are a couple of helpful links:

[http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

