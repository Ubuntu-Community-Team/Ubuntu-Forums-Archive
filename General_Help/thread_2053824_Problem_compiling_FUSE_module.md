---
title: "Problem compiling FUSE module"
date: 2012-09-06
forum: General Help
---

### Post by arttykh on 2012-09-06
Hi all,

I am trying to compile the FUSE module for linux-2.6.35.13

I have downloaded fuse v. 2.7.0 from [*http://fuse.sourceforge.net/*](*http://fuse.sourceforge.net/*) and linux-2.6.35.13 source from [*http://kernel.org*](*http://kernel.org*).

I have tried to compile by this by following the instructions from [*http://fuse.sourceforge.net/*](*http://fuse.sourceforge.net/*). (I created a .config file and placed it in the kernel source directory.)

But, when I run:

```
~/fuse-2.7.0/$ ./configure --with-kernel=~/linux-2.6.35.13/
```


I've got the following error:

```
checking kernel source directory... /home/at/tv/linux-2.6.35.13/
checking kernel build directory... /home/at/tv/linux-2.6.35.13/
checking kernel source version... Not found
configure: error:
	*** Cannot determine the version of the linux kernel source. Please
	*** prepare the kernel before running this script
```


Now i'm stuck.

Has anyone got any ideas?

---

### Post by dino99 on 2012-09-06
*** source version... Not found  ***

so is kernel source installed ?

This needs first to activate the source archive, then install the kernel source. Check it with synaptic for easier reading.

---

### Post by arttykh on 2012-09-06
> so is kernel source installed ?

I have downloaded kernel 2.6.35.13 source and extracted the kernel source to special directory (as it said in official site).

Than i specified kernel source directory using *--with-kernel* option.

---

