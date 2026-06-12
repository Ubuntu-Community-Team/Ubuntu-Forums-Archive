---
title: "compiling fvwm - no internet connection"
date: 2005-02-04
forum: General Help
---

### Post by josh on 2005-02-04
hi guys! 

i have no internet connection with my ubuntu computer so i cannot do an "apt-get install fvwm" what i did is i downloaded from antoher computer, the source tarball of fvwm and i tried compiling it. after untarring it, i issued "./configure" and it was running fine til it hit X.

checking for X... no

X11 libraries or header files could not be found. Please make sure the X11 development package is installed on your system. if it is definitely installed, try setting the include and library paths with the --x-include and --x-libraries options of configure. Fvwm can not be compiled without the X11 development environment.

--end of error--

well, i dont know what to "apt-get install" from the cd i installed x-window-system-core, xserver-xfree86, gcc, g++. i do not know what the or where the X11 libraries are located. the error said that i should have them installed. where do i get those libraries for X11? or is there another way for me to install fvwm?

thanks in advance! 

regards,
josh

---

### Post by valadil on 2005-02-04
You got all the libraries you need to run fvwm but to compile it you also need the source code of those libraries.  Try grabbing the -dev versions of those libs.

Also, you still can use apt without having the intarweb.  Well, not apt, but dpkg specifically.  All that apt does is make a list of packages that will need to be installed, download the .deb of that package, then run it through dpkg.  If you were to get a list of said packages you could go to the repository yourself, dl those files, and transfer them to the other computer.  It sounds tedious but in some cases it may be easier than dealing with source code for a bunch of packages.

---

### Post by josh on 2005-02-04
[QUOTE=valadil]You got all the libraries you need to run fvwm but to compile it you also need the source code of those libraries.  Try grabbing the -dev versions of those libs.

Also, you still can use apt without having the intarweb.  Well, not apt, but dpkg specifically.  All that apt does is make a list of packages that will need to be installed, download the .deb of that package, then run it through dpkg.  If you were to get a list of said packages you could go to the repository yourself, dl those files, and transfer them to the other computer.  It sounds tedious but in some cases it may be easier than dealing with source code for a bunch of packages.[/QUOTE]
 thanks for the quick reply valadil!

could you please tell me which specific libraries are needed? i did a search on google regarding "fvwm dev libraries" but found nothing. even int he fvwm.org i found no libraries there. where should i get those?

i would try downloading the .deb package of fvwm.

have you any links on how to use dpkg? im new to ubuntu and have no background in debian.  i find it hard to look for tutorials in dpkg because of this limited internet connection. thanks a lot!

regards,
josh

---

