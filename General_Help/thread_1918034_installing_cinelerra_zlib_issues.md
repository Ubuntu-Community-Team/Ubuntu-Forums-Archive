---
title: "installing cinelerra zlib issues"
date: 2012-01-31
forum: General Help
---

### Post by collapsing wave on 2012-01-31
Hi
trying to install cinelerra 4.3
installed zlib 1.2.5 when prompted then I get this message

checking for ANSI C header files... (cached) yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking for compress in -lz... no
configure: error:
*** OpenEXR requires a recent version of zlib, which you don't appear to
*** have.
***
*** This could be because the run-time linker is not finding zlib, or it
*** is finding the wrong version.  In this case, you'll need to set your
*** LD_LIBRARY_PATH environment variable, or edit /etc/ld.so.conf to point
*** to the proper version.  Also, make sure you have run ldconfig if
*** that is required on your system.
			   
Giving up and going to a movie.
rus@rus-ubuntu-laptop:~/cinelerra-4.3$ 

And I'm out on the edges of what I know. Can anyone give me help with the next step as I don't understand what this means

---

### Post by raja.genupula on 2012-01-31
the easiest way i can give you as add its PPA to your repo list and then install it either from software center or synaptic . they will deal with remaining Job . 

[https://launchpad.net/~cinelerra-ppa/+archive/ppa?field.series_filter=oneiric](https://launchpad.net/~cinelerra-ppa/+archive/ppa?field.series_filter=oneiric)

All the best .

---

### Post by collapsing wave on 2012-01-31
Perfect and simple. Thank you very much.
Ubuntu is becoming much easier for idiots like me to use.

---

### Post by raja.genupula on 2012-01-31
Hi man , welcome . please don't be negative to yourself , always be positive . 

Everything will be fine .

---

