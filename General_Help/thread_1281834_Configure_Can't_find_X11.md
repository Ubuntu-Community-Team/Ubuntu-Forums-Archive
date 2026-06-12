---
title: "Configure Can't find X11 ?"
date: 2009-10-03
forum: General Help
---

### Post by Lyuokdea on 2009-10-03
I'm trying to build a public nasa science tool, but am unable to install it correctly on ubuntu. While running configure I get the error:


checking for X... no
configure: error: One or more components requires X11!


Obviously, I have x11 on this computer, is there some other package it could be looking for? I'm running Ubuntu 9.04 standard

Thanks,

~Lyuokdea

---

### Post by dearingj on 2009-10-03
You have all the files you need to run X11 apps, but you don't have what is needed to compile X11 apps. I'd recommend opening up Synaptic Package Manager, searching for packages with "x11" in the name, and then visually scanning the list for names ending in "-dev". I don't know which specific packages you will need. You'll also want to install "build-essential" if you haven't already.

---

### Post by Lyuokdea on 2009-10-03
perfect! Thanks

~Lyuokdea

---

### Post by dearingj on 2009-10-03
Sounds like it worked :)
Out of curiosity, which package(s) did you have to install to get it working?

---

### Post by Lyuokdea on 2009-10-03
not sure which one did it, i installed about 10 devs in a batch, and then it worked.

another question though, cause I came back to this still having problems: is there a way to install the f90 fortran compiler? I have gfortran and ifort already, but for some reason, it seems to very specifically want f90

~Lyuokdea

---

