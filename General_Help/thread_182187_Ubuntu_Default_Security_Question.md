---
title: "Ubuntu Default Security Question"
date: 2006-05-25
forum: General Help
---

### Post by jpoe on 2006-05-25
I was playing with some memory monitoring software on my local machine today and I noticed something peculiar.  It seems Ubuntu has a linux patch to randomize the location of environmental variables?

I quickly did a few google searches and found that a kernel patch called PaX does something like this, but I haven't been able to find any information about the default Ubuntu Linux install.  Does anyone know if this is indeed the case?  I compared it to a few other distros and none of them seem to be employing the memory randomization feature.  

I think this is great, and I was wondering if anyone knew about this; or where I could read up on Ubuntu's implementation in more detail?  Thanks in advance.

---

### Post by bernardfrancois on 2006-05-25
You could get the kernel source from synaptic and check if it contains that patch's code...

Which memory monitoring program did you use? It sounds fun to play around with.

---

### Post by jpoe on 2006-05-26
Hm, only thing is, I'm not completely certain which patch it came from.  It doesn't seem as thought all of the PaX stuff is being used, and that was pretty much just a guess anyway.  I was more wondering if anyone knew where to find such information about the distro.  I know, for example, that this enhancement isn't in Debian Sarge (one of the other distros I tested).

As for the memory tools, specifically at the time I discovered this I just used a  printf("%p",getenv(var)) to print out the memory address of the environmental variable and noticed it was different on every run (this would normally change fairly infrequently, perhaps if more environmental variables were added or changed, or if the name of the program changed).

A lot of my work has to do with making architecture changes on Alpha systems though, so I am confined mostly to what still works on alpha systems.  I use full cycle level simulators such as M5 and SimpleScalar, but if you just want a look into the memory tools like gdb and valgrind can be much fun too ... =)

---

