---
title: "Can't install powertop 2.0"
date: 2012-07-25
forum: General Help
---

### Post by misterBubbles1 on 2012-07-25
Hi guys, 
I tried following the directions to installing powertop 2.0, as described by the readme file
 >    ./autogen.sh
    ./configure 
    ./make
    ./make installWhen I run ./autogen.sh, I get the output

> autoreconf: Entering directory `.'
autoreconf: running: autopoint
autoreconf: running: aclocal -I m4
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'
I don't really know what it means. I continue on and run ./configure. Most of the output says yes, but there are some things that say no. I then run ./make. it says
> ./make: No such file or directoryI do have a Makefile, Makefile.am, and Makefile.in in my powertop directory though.

Why won't ./make run through? Why don't I have a make file? 

I am currently using gnome under Ubuntu 12.04.

---

### Post by galvatron408 on 2012-07-28
"make" sure you have the correct permission. (pun intended) i.e. perhaps you need to use sudo.

---

### Post by misterBubbles1 on 2012-07-29
I tried all the above commands with sudo in front, but there was no change. I'm stuck.

---

### Post by raja.genupula on 2012-07-29
hey actually you have to type the commands like this

```
./configure

make 

sudo make install 
```

---

