---
title: "Where to find my source file"
date: 2009-11-11
forum: General Help
---

### Post by chabos9 on 2009-11-11
First things first, which is basic info.
Kernel: 2.6.28-11 according to uname-r
OS: Ubuntu version 9.10

I'm trying to install virtual box so I can boot a raw partition, but I'm having some trouble with the install.  Here is the message I'm getting.
> Error! Your kernel source for kernel 2.6.28-11-generic cannot be found at
/lib/modules/2.6.28-11-generic/build or /lib/modules/2.6.28-11-generic/source.
I went to the 2.6.28-11-generic folder, and sure enough there was no build or source folder inside.  I did notice that there is another folder called /lib/modules/2.6.31-14-generic, which did have a build folder.  Inside the build folder, there is a file called source, but it is a link and I get an error message saying the location the link refers to doesn't exist.  I checked with uname -r, and that said my kernel was 2.6.28-11 generic, the one without the build folder.  Does any one know where my source is and how to point virtual box to it?
Thanks.

---

