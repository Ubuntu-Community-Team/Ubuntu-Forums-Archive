---
title: "multiple gcc versions side-by-side"
date: 2010-05-27
forum: General Help
---

### Post by Alex Flint on 2010-05-27
I would like to experiment with gcc 4.5, while leaving the current gcc 4.4.3 installed. I plan to download and compile gcc 4.5 manually, but I was wondering what the best way is me to install it  without interfering with gcc 4.4.3. I am happy for gcc 4.4.3 to be found by default -- I only want to try compiling some toy programs with gcc 4.5.

I'm running Ubuntu lucid.

---

### Post by curts on 2011-01-06
I have not explicitely done this (yet) in Linux, but the way I handled this in Solaris was to install the alternate version of gcc to /usr/local/gcc_x.y.z.  I configured a shell alias (i.e. go_gccxyz) that would prepend the appropriate bin and lib paths to my shell environment when I wanted to use the alternate version.  Project Makefiles would simply point to the /usr/local/gcc_x.y.z paths via suitable abstraction variables.

In Linux you have the option of changing the alternatives link, but I don't find that to be practical if you want to frequently switch between gcc versions.  I see the alternatives link as representing the current system default.

Hope this helps,

Curt

---

