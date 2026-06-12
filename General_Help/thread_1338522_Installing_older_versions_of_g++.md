---
title: "Installing older versions of g++"
date: 2009-11-26
forum: General Help
---

### Post by Gonchos on 2009-11-26
I need to install 4.3.2 version for a uni project, but I only know how to download and install the latest version running "apt-get install ... " 

I have downloaded a .tar.gz file from [http://gcc.gnu.org/mirrors.html](http://gcc.gnu.org/mirrors.html) but I don't know how to install it in my PC. 

Thanks :)

---

### Post by sedawk on 2009-11-26
I think you not only need the right compiler, but you
might also need the correct libraries, otherwise your
software might not work on the other PC.

To solve this you can either use static linking (big binaries
with everything they need included) or you
can work at home with any gcc version but then
you have to recompile the source on the uni box
to check it is compatible with the other gcc version.

(If you know the Linux distribution the uni uses you
 can also setup a small virtual PC or setup a dual boot
 system and install the correct distribution in parallel.
 Then you have a better chance that not only gcc has
 the correct version!).

---

