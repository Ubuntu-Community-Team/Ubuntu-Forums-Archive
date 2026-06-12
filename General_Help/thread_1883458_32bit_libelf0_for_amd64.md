---
title: "32bit libelf0 for amd64"
date: 2011-11-19
forum: General Help
---

### Post by ggwhaite on 2011-11-19
I've just installed kubuntu 11.10 64bit version. I want to run a 32bit game (Neverwinter Nights) so I installed the ia32-libs package. Unfortunately this package does not contain a 32bit version of libelf0. Does anybody know where I can get a 32bit version of libelf0 for a 64bit system?

---

### Post by ggwhaite on 2011-11-20
I solved the problem by downloading the i386 version of the libelfg0 package, extracting the library file to a subdirectory in the game's directory, added the subdirectory to the LD_LIBRARY_PATH environent variable before launching the game. Now I can play the game and I'm happy.

---

