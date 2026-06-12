---
title: "Compiling options(and compiler) used in compiling ubuntu packages"
date: 2010-10-29
forum: General Help
---

### Post by San_SS! on 2010-10-29
Hi all,

I'm trying to compile a the source of a package(downloaded via apt-get source) but the resulting binary is different than the one installed via *apt-get install*.

I'm compiling it with ./configure and after that make.

But I'd like to know which options and which compiler, in case other than gcc is being used, are being used to compile the packages in the repository.

Thanks in advance

---

### Post by mc4man on 2010-10-29
Sometimes a plain ./configure doesn't fully enable a build or other possible build options. (./configure --help can be informative
If the source you're building is avail. in the ubuntu or a ppa repo then a couple of ways to see how it's built.

create a folder, cd to it and apt-get source packagename

Look thru the /debian folder for info (control, rules, confflags, ect.

You could do a search w/ keywords - appname source launchpad, from the source page eventually you can find and view the build log for any ubuntu repo package (or ppa

(what package were you building?

---

### Post by San_SS! on 2010-10-29
I'm trying to build mpg123. And now that you say that, i can see that in debian/rules there are things like:
CONF_COMMON:=--prefix=/usr --enable-static --enable-shared --disable-ltdl-install

I guess that one is the one those are the arguments used in the ./configure call.

and there are CFLAGS to, that i guess are the flags to pass to the compiler, right?

Thanks a lot!

---

### Post by mc4man on 2010-10-29
In this case I'm not too sure I'd pay too much attention to how ubuntu builds (though do profess some ignorance about mp3's and mpg123

Depending on your usage you may get a better build specific to your hardware by looking thru ./configure --help. maybe some reading at the mpg123 site. and do do builds and see..

A quick glance  and I'd be inclined for starters to use here something like this (maverick - mpg123 version 1.12.5

./configure  --enable-static  --with-cpu=i586_dither --with-optimization=3   --enable-int-quality --enable-aligncheck=no

and install w/ a simple checkinstall comm.

```
sudo checkinstall  --backup=no --default --deldoc=yes \
--deldesc=yes --delspec=yes --fstrans=no
```

---

