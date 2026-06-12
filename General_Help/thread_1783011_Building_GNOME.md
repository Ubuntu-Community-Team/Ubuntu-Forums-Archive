---
title: "Building GNOME"
date: 2011-06-15
forum: General Help
---

### Post by UART16550 on 2011-06-15
I want to build my own GNOME. The problem I have is that I cannot find the tarball for the GNOME source code.

Another thing I've read on their website is that the way to build it is not the conventional './configure, make, make install', and that it has to be done using a multi-phase process. Is this correct?

---

### Post by Bandit on 2011-06-15
> **UART16550 said:**
> I want to build my own GNOME. The problem I have is that I cannot find the tarball for the GNOME source code.

Another thing I've read on their website is that the way to build it is not the conventional './configure, make, make install', and that it has to be done using a multi-phase process. Is this correct?

Thats because its like a huge amount of files that have to go into it. Each piece of the desktop from the taskbar to nautilus and even gtk must all be compiled individually in a specific order for it all to compile or you will run into dep errors. I got it to all compile 6 years ago and swore to never bother again. Many files also end up having their dependencies intertwinned making it almost impossible to compile at time unless you compiling new files on a older machine that already has gnome and its dev libs installed. Thats a huge reason they went to Gnome 3. A Fresh slate.. :-)

EDIT: See if they have Garnome still up. Its your best option if it still is.

---

### Post by UART16550 on 2011-06-15
How is GNOME 3 a new slate? Is it much easier to compile and use?

What is 'Garnome'?

I am going to build my own Linux system from scratch.

---

