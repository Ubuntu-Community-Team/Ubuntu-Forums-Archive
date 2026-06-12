---
title: "Using window's programs while on ubuntu"
date: 2011-07-20
forum: General Help
---

### Post by jcast1008 on 2011-07-20
Is it possible to use the programs installed on the windows xp partition when i boot into ubuntu os?

---

### Post by 3Miro on 2011-07-20
The short answer is "maybe".

You can take a look at both "wine" and "VirtualBox". 

Wine lest you run windows programs under Linux and while not all programs work, those that do usually work pretty well. I myself enjoy several windows games that I play from within Ubuntu. Wine can be tricky to setup, especially for some programs, you have to look at it on a program-by-program basis.

VirtualBox lets you install a copy of windows that will run within Ubuntu. This method will not let you do graphics extensive apps, however, the low graphics apps will work near flawlessly.

---

### Post by jocko on 2011-07-20
In general: No. You may be able to run some directly from the windows install through wine, but most applications are too deeply dependent on the windows registry and on being properly installed in the system you run them on...

But you can install many windows applications in ubuntu using wine. Some programs work very well, others work mostly well with a few bugs while many don't work at all. Check out the [Wine Application Database]("http://appdb.winehq.org/") to see what is tested, what works and what does not work.

---

