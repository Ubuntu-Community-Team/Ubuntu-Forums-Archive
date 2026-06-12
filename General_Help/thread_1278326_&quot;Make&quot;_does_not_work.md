---
title: "&quot;Make&quot; does not work"
date: 2009-09-29
forum: General Help
---

### Post by amcavoy on 2009-09-29
I am trying to install a package and when I type ./configure, everything seems to be working correctly in the terminal.  However, when I type "make", I get the following error:

alex@alex-desktop:~/Desktop/swfdec-mozilla-0.8.2$ make
make: *** No targets specified and no makefile found.  Stop.

I have installed "make."  Does anyone know what is wrong?

---

### Post by bruno9779 on 2009-09-29
Probably it does not use make to compile maybe scons, maybe cmake, maybe something else.

Check the INSTALL file, if there is one, there it should state which command to use

---

### Post by bruno9779 on 2009-09-29
I have dowloaded the package, and i can see makeinstall there, are you sure that you are in the right folder?

by the way, the newest stable release of swfdec is 0.8.4, apparently it has better youtube support

---

### Post by amcavoy on 2009-09-29
> **bruno9779 said:**
> I have dowloaded the package, and i can see makeinstall there, are you sure that you are in the right folder?

by the way, the newest stable release of swfdec is 0.8.4, apparently it has better youtube support

Thanks for the reply.  Yeah, I'm in the right folder; it just doesn't work.  I'll try a different program I guess...

---

### Post by hxleet on 2009-09-29
> **amcavoy said:**
> I am trying to install a package and when I type ./configure, everything seems to be working correctly in the terminal.  However, when I type "make", I get the following error:

alex@alex-desktop:~/Desktop/swfdec-mozilla-0.8.2$ make
make: *** No targets specified and no makefile found.  Stop.

I have installed "make."  Does anyone know what is wrong?

Just use your synaptic package manager and search swfdec-GNOME and mozilla and install them that way

hxleet

---

