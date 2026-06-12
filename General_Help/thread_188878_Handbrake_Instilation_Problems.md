---
title: "Handbrake Instilation Problems"
date: 2006-06-04
forum: General Help
---

### Post by morpheus2485 on 2006-06-04
I'm trying to install HandBrake so that i can rip DVD's to my shiny new ipod video, but when I run jam to try to install it, I get the following error.  I've searched for answers on google but didn't come up with anything.


```

# pwd
/home/kristine/Desktop/HandBrake-0.7.1
# jam
...found 175 target(s)...
...updating 45 target(s)...
LibA52 contrib/lib/liba52.a
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... no
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables

    cd `dirname contrib/a52dec.tar.gz` && CONTRIB=`pwd` &&
    rm -rf a52dec && tar xzf a52dec.tar.gz && cd a52dec &&
    ./configure --prefix=$CONTRIB && make && make install &&
    strip -S $CONTRIB/lib/liba52.a

...failed LibA52 contrib/lib/liba52.a ...
LibAvCodec contrib/lib/libavcodec.a
...interrupted
...failed updating 1 target(s)...

```

any ideas?

---

### Post by rbalfour on 2006-06-04
Have you installed the Build-essential?

try 
> sudo apt-get install build-essential

then recompile handbrake.

---

### Post by morpheus2485 on 2006-06-04
yes, that fixed it.  

thanks!

---

### Post by thegrayarea on 2006-07-09
the download i got doesn't even have a "jam" file to build, do you have a link to the download you are using to install handbrake?

thanks,

thegrayarea

---

