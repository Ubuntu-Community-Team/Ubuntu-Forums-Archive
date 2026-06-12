---
title: "How to reduce memory usage / footprint in 10.04"
date: 2010-05-15
forum: General Help
---

### Post by allandeamon on 2010-05-15
Hi. I like a lot of the last Ubuntu editions, but my computer is a little old, and Ubuntu becomes slower each edition to me. 

I get a AMD Athlon 2 GHz, with just 512 MB of RAM memory...

I tried to customize my last installation of 9.10, but i just mess up with the OS. Well, I googled for informations about reducing memory usage, as well others speed-ups but all them are a bit older. Does anyone know any resource about this?

Until now I just disabled startups programs, but i really want is remove packages and everything that I don't use.

One thing thats get me up set sometimes is that I run Win XP pro under a cryptographed partition, and even yet its very fast in my PC. I even tried Windows 7, and its was faster than the Ubuntus I installed. 

When I'm using the 10.04, there is a lot of memory used by cache, specially Gnome...

Any suggestion?

---

### Post by Sin@Sin-Sacrifice on 2010-05-15
You could also try a minimalist distro like [lubuntu]("http://lubuntu.net/"). Otherwise remove everything that your system doesn't need. Only you know your hardware so you'll have to research what gets used and what's just wasting space/ram. There are also even more minimalist Linux distros like arch or knoppix but they are more difficult to configure. Nothing you couldn't learn with a little googling though. If you plan to move to something like arch you may want to familiarize yourself with the command line interface because they install without a GUI (gnome, LXDE, KDE, etc...). I think ubuntu with lxde (lubuntu) would suffice without all the research though.

Edit: Info on minimal linux distros [http://wiki.laptop.org/go/Minimal_Linux_distros](http://wiki.laptop.org/go/Minimal_Linux_distros)

---

### Post by warfacegod on 2010-05-15
A little old... With a 2 GHz AMD and half a GB of RAM, I'm going to guess at least five years old. Your computer may just be getting tired.

LXDE is a good choice. You can install it from Synaptic and your system will "become" Lubuntu. Just change the Session to LXDE before you finish logging in.

SliTaz is another way to go. Its incredibly fast. Small with only a 30 MB .iso and has a complete GUI. Its got a rather steep learning curve though. Then again so do most of the truly lightweight distros like Puppy Linux or Damn Small Linux.

I know just the guy to have suggestions. I'll send him a link.

---

### Post by nikolaynag on 2010-07-01
I have similar problem with a laptop based on intel celleron processor and limited to only 512 MB of RAM. 

Minimalistic distros is not a good solution. Yes, they are fast, but have much more bugs (because they are less tested) and require much more efforts to workaround problems.  They are good for advanced users, but not for beginners in Ubuntu and GNU/Linux world.

I believe there must be another solution, because 9.10, Windows XP and even Windows 7 require less RAM. Maybe somebody knows a simple and effective memory reduction methods for 10.04? I dont want disable small daemon processes, releasing few hundred kilobytes, that is ineffective. More interesting is to figure out why each gnome applet eats about 5 MB of RAM? And gnome-panel eats more than 10 Mb? Maybe here is the problem and the solution?

---

