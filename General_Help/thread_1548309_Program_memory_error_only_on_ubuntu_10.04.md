---
title: "Program memory error only on ubuntu 10.04"
date: 2010-08-08
forum: General Help
---

### Post by bagpussnz on 2010-08-08
Hi,
This is a strange one...
I have an old program we've used for about 15 years. It is a Fortran to C translator. Over the years, we've used it on everything (AIX, HPUX, MPE/ix, VMS, SCO and Linux) to translate our legacy Fortran code to C for standard compilation on various platforms.

However, we've just moved our development to Ubuntu 10.04. And we find the program is starting to have memory errors. (Some of the translated code is garbage). It worked fine on Ubuntu 9.10 and previous versions.
I've reproduced it on all machines - whether ext3 or ext4 is used (yes, I even tried that).

I do have the source code for the application, but it's very complicated. Before I start stepping through the code to look for differences, I thought I'd ask if anyone has any ideas.

Note: I've tried compiling the translator code on ubuntu 10.04 - and also copying the linked application from a previous version. Both produce the garbage code - and it's always in exactly the same places.

Cheers,
Ian.

---

