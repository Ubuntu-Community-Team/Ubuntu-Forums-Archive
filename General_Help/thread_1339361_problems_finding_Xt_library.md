---
title: "problems finding Xt library"
date: 2009-11-27
forum: General Help
---

### Post by shortmort37 on 2009-11-27
I'm trying to install gatos-0.0.5 to get my ATI AIW card working.  I'm running 9.10, and when I run ./configure, I get this in config.log:

configure:4847: gcc -o conftest -g -O2   conftest.c -lXt  1>&5
/usr/bin/ld: cannot find -lXt

I've read that installing libx11-dev should give me the X libraries, but apt-get claims I already have the latest.  I know I don't have a /usr/lib/X11R6 dir, and a find on libXt.a yielded nothing.

Whaddup?

adTHANKSvance
Dan

---

### Post by Virtual Liberty on 2009-11-27
[libxt-dev]("http://packages.ubuntu.com/karmic/libxt-dev") should be what you are looking for.

---

### Post by shortmort37 on 2009-11-27
Well, that helped!  I got further.  But it's still looking for libs in X11R6, apparently:

configure:5633: checking for ibtk/ibox.h
configure:5644: gcc -E  conftest.c -I/usr/X11R6/include >/dev/null 2>conftest.out
configure:5639:23: error: ibtk/ibox.h: No such file or directory

Dan

---

### Post by Virtual Liberty on 2009-11-27
[libibtk-dev]("http://packages.ubuntu.com/intrepid/libdevel/libibtk-dev") ?

---

### Post by shortmort37 on 2009-11-27
That did it!  Thanks.

---

