---
title: "Can't configure programs to install them."
date: 2006-03-03
forum: General Help
---

### Post by thomas505 on 2006-03-03
Hi i'm recently installed Breezy Gnome and was trying to install a program from source when after typing ./configure i got:
configure: configuring for GNU Wget 1.10.1
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
does anyone know how to correct this?
I've tried uninstalling and reinstalling gcc but that didn't work???
Any and all help would be appreciated.

---

### Post by RAOF on 2006-03-03
Have you installed the "build-essential" package?  That contains what (most) programs need to build successfully.

Secondly, the generic "what are you trying to install?" question.  Is compiling from source really necessary?  Is it (or a program equivalent to it) available in one of the Ubuntu repositories?

---

### Post by thomas505 on 2006-03-03
Thanks that has gotten me alot furthur though i'm still getting errors. I'll see if i can get them via apt-get. Also in response to your question the reason i was compiling from source is because i can download it at school then bring it home whereas if i were to do it at home (i have dial up) it would take hours.

Edit:
The errors i am getting on the thing i have tried to install is:
configure: error: Configure could not find required X11 libraries(at the end of typing ./configure)
configure: error: Configure could not find required X11 libraries
make: *** [makeinclude] Error 1(after typing make)
Can you tell me how to correct this. 
Thank you for your patience.

---

### Post by RAOF on 2006-03-03
Actually, you can download the .debs at school and install them at home.  No compiling necessary :).  Just check out [packages.ubuntu.com](packages.ubuntu.com)

Compiling from source is going to be unnecessarily painful.  Especially since you'll end up apt-getting a lot of development libraries (which are probably bigger than the original package) anyway.

---

