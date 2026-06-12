---
title: "Scratch program for kids"
date: 2010-01-28
forum: General Help
---

### Post by Jbike on 2010-01-28
Have I a puzzle for you. In fully updated 9.10 machines, I installed scratch, a great programming environment for kids from MIT on my 64 bit Athlon (or tried to ), my netbook and my 32 bit desktop by adding the following in software sources: 

ppa:scratch/ppa

You can get the instructions here:

[http://info.scratch.mit.edu/Linux_Installer](http://info.scratch.mit.edu/Linux_Installer)

Here is the puzzle. With my atom netbook and my 32 bit Athlon, scratch appears in synaptic, installs and runs perfectly. Not so with the 64 bit Athlon 64 duel core. Scratch does NOT appear in synaptic? Does anyone know why? 

Thanks Jbike

---

### Post by lapcat66 on 2010-02-03
Hi JBike,
I had a similar experience installing scratch in 32-bit jaunty.  After adding the ppa and updating, Scratch did not appear in Synaptic when searching for 'scratch'.  

However, when I clicked on Synaptic's right-panel "ppa.launchpad.net/main", Scratch is there, and installs properly.

Searching for words in the description doesn't seem to find Scratch either, so I guess it's not getting entered into the database properly.

Not sure if that's related to your experience.

It has the description:
Scratch is an easy, interactive, collaborative programming
environment designed for creation of interactive stories, animations, games, music, and art -- and sharing these on the web.  Scratch is designed to help young people (ages 8 and up) develop 21st century learning skills. As they create Scratch projects, young people learn important mathematical and computational ideas, while also gaining a deeper understanding of the process of design.

---

### Post by n0dix on 2010-02-03
> **Jbike said:**
> Have I a puzzle for you. In fully updated 9.10 machines, I installed scratch, a great programming environment for kids from MIT on my 64 bit Athlon (or tried to ), my netbook and my 32 bit desktop by adding the following in software sources: 

ppa:scratch/ppa

You can get the instructions here:

[http://info.scratch.mit.edu/Linux_Installer](http://info.scratch.mit.edu/Linux_Installer)

Here is the puzzle. With my atom netbook and my 32 bit Athlon, scratch appears in synaptic, installs and runs perfectly. Not so with the 64 bit Athlon 64 duel core. Scratch does NOT appear in synaptic? Does anyone know why? 

Thanks Jbike

Maybe because threre is not a 64-bit version of the program. I'm not sure, only guessing.

---

### Post by gatman3 on 2010-02-21
Yeah, the problem is that the ppa that they provide is for 32-bit ubuntu.  I haven't been able to find a 64-bit ppa, probably doesn't exist.  Unfortunately this is not a maintained package for ubuntu, so you get what you get with the ppa.  I've started looking a little bit into compiling it from scratch, but unfortunately it doesn't look trivial.  I have also read that the windows version doesn't run great under wine, either.  For now I am going to play with this package under VMware and then decide if I want to invest time in compiling for 64-bit.

---

### Post by n0dix on 2010-02-22
> **gatman3 said:**
> Yeah, the problem is that the ppa that they provide is for 32-bit ubuntu.  I haven't been able to find a 64-bit ppa, probably doesn't exist.  Unfortunately this is not a maintained package for ubuntu, so you get what you get with the ppa.  I've started looking a little bit into compiling it from scratch, but unfortunately it doesn't look trivial.  I have also read that the windows version doesn't run great under wine, either.  For now I am going to play with this package under VMware and then decide if I want to invest time in compiling for 64-bit.

maybe, the best option in to run the program in VMware for now.

---

### Post by Jbike on 2010-02-24
Do I have questions. The following posts contain linux relevant instructions (the first background information only):

[http://scratch.mit.edu/forums/viewtopic.php?id=21](http://scratch.mit.edu/forums/viewtopic.php?id=21)
[http://scratch.mit.edu/forums/viewtopic.php?id=21&p=2](http://scratch.mit.edu/forums/viewtopic.php?id=21&p=2)   which point to here-
[http://info.scratch.mit.edu/Source_Code](http://info.scratch.mit.edu/Source_Code)

 for installing from source... where I am assuming we do the usual:

 .configure make make install

The posts discuss a linux version as unavailable, yet Jens (from the link above) points to the full source code??? If I have the source, why do I need a squeakVM? Maybe I need to learn a thing or two about squeak. 

 I am also confused with the requirement to use the squeak VM, and even more confused about what to do with the mentioned plugins. Why was functionality removed from the source package, specifically the project sharing code? My son just Loves that friends can come over and each can interact with the same game. 

Does anyone have definitive instruction to install scratch from source on a 64bit os?

Thanks,
Jbike

---

