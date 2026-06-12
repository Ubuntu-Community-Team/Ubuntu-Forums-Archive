---
title: "gaim 1.1.3"
date: 2005-02-23
forum: General Help
---

### Post by earobinson on 2005-02-23
anyone got an instlation for gaim 1.1.3?

thanks

---

### Post by acascianelli on 2005-02-23
[QUOTE=earobinson]anyone got an instlation for gaim 1.1.3?

thanks[/QUOTE]
 it hasnt been update yet on the ubuntu distribution tree.  does anybody know any other good sources to use with synaptic to get more frequently update packages?

i know it wouldnt be very hard to download the debian package or the source for gaim 1.1.2 but id like to keep everything going thru synaptic if i can.

---

### Post by earobinson on 2005-02-24
ya im using 1.1.0 so 1.1.2 or 1.1.3 would be nice,  can no one compile these on there own and poste them?

---

### Post by panabar on 2005-02-24
You could use unstable Debian repositories with synaptic but I won't recommend that. They are updated frequently but some of the packages there mess up your warty installation and possible updates from warty security repository. 
(I broke a very stable warty installation with packages from unstable debian :( )

If you can try compiling new packages and installing with checkinstall.

Or even better than unstable Debian packages you can give Hoary (uses gaim 1.1.2-3ubuntu1) a try, but beware it's still under development!

---

### Post by earobinson on 2005-02-24
[QUOTE=panabar]You could use unstable Debian repositories with synaptic but I won't recommend that. They are updated frequently but some of the packages there mess up your warty installation and possible updates from warty security repository. 
(I broke a very stable warty installation with packages from unstable debian :( )

If you can try compiling new packages and installing with checkinstall.

Or even better than unstable Debian packages you can give Hoary (uses gaim 1.1.2-3ubuntu1) a try, but beware it's still under development![/QUOTE]
 thanks any way i can add only gaim and not everything else?

---

### Post by irtehjabbit on 2005-03-03
[QUOTE=earobinson]anyone got an instlation for gaim 1.1.3?

thanks[/QUOTE]

OK, this is how I installed Gaim 1.1.4

1) Install GNU TLS Library (devel)
usung Synaptic search and install -> libgnutls-10-dev

2) Download gaim 1.1.4 source code from gaim.sf.net

3) Build gaim

$ ./configure --enable-gnutls=yes
$ make

4) Install gaim with debian package support

$ sudo checkinstall

That's all!

Hope it helps

---

### Post by pavkonti on 2005-03-04
> 4) Install gaim with debian package support 
how to make this?

```
sudo make install
``` 

or something else? I install it but I did not have sounds, only my pc speaker works..

---

### Post by bored2k on 2005-03-04
> checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details. 

>  # apt-get install cpp
Reading Package Lists... Done
Building Dependency Tree... Done
cpp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 87 not upgraded. 

Any help ??


EDIT: Nevermind , i needed build-essential .

---

