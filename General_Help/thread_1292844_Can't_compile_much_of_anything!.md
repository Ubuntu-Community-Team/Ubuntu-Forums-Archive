---
title: "Can't compile much of anything!"
date: 2009-10-16
forum: General Help
---

### Post by karimruan on 2009-10-16
I have a feeling I am missing a lot of libs on my computer. I have never had this issue before in any of my previous installs. Here is what I get when trying to ./configure gtk+-2.12.12:



checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.13.5    atk >= 1.9.0    pango >= 1.17.3    cairo >= 1.2.0) were not met:

No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

mat@mat-laptop:~/Desktop/gtk+-2.12.12$ 




When I try to ./configure LIVES, It tells me I need the GTK package. But i can't even install that! Is there any way to check the sanity of my system??????

EDIT: I am running 9.04

---

### Post by karimruan on 2009-10-16
Okay, I installed everything it said to compile in my above post, and THINK I installed GTK, but when I try to ./configure LIVE, it still gives me this error:

checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.4.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

mat@mat-laptop:~/Programs/lives-1.1.3$ 


I found another post in the forums like this, but it didn't really help. I guess I don't know how to install the gtk+-2.0 package. I though I just installed the latest version, but it didn't work. Can anyone point me to a download or something, or give me an exact name i could use in apt or synaptic???

Thanks ahead of time!

---

### Post by mc4man on 2009-10-16
libgtk2.0 is part of your 'base' system libs, I believe jaunty uses 2.16. so not sure what you were doing, have done with 2.12 (what's used on hardy

You were/are missing the -dev, -  this will, would of taken care of
```

sudo apt-get install libgtk2.0-dev
```

edit: note that everything needed for Lives is available from jaunty repos thru apt-get

---

### Post by karimruan on 2009-10-16
Thanks Mc4Man, that got me further. I (think I) successfully configured Lives, but when I run make, I get this output:


main.c: In function ‘lives_init’:
main.c:1483: error: invalid storage class for function ‘lives_startup’
main.c: In function ‘lives_startup’:
main.c:1511: warning: passing argument 1 of ‘lives_init’ from incompatible pointer type
main.c: In function ‘lives_init’:
main.c:1672: warning: ‘main’ is normally a non-static function
main.c: In function ‘main’:
main.c:1675: error: request for member ‘ign_clipset’ in something not a structure or union
main.c:1675: error: request for member ‘ign_osc’ in something not a structure or union
main.c:1675: error: request for member ‘ign_jackopts’ in something not a structure or union
main.c:1675: error: request for member ‘ign_aplayer’ in something not a structure or union
main.c:1767: error: request for member ‘ign_clipset’ in something not a structure or union
main.c:1774: error: request for member ‘ign_clipset’ in something not a structure or union
main.c:1808: error: request for member ‘ign_aplayer’ in something not a structure or union
main.c:1822: error: request for member ‘ign_osc’ in something not a structure or union
main.c:1828: error: request for member ‘ign_osc’ in something not a structure or union
main.c: In function ‘lives_init’:
main.c:2559: error: invalid storage class for function ‘get_max_opsize’
main.c:4157: error: expected declaration or statement at end of input
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/mat/Programs/lives-1.1.3/src'
make: *** [install-recursive] Error 1


Sorry for posting so much code, I didn't know if it was all needed or just the last few lines. Anyway, I can't make sense of this. 

Again, and again, thank you for the help! Like I said, I always compiled from source in my last install. Funny story actually, my 1 1/2 year old son deleted my partition table. Have NO IDEA HOW.

Anyway, any help with this compilation issue would be appreciated!

---

### Post by mc4man on 2009-10-18
Your error message is slightly out of context so don't know ( need to go back a ways to a 'entering,,' or similar

2 things I remember from last yr. when I built it...
If you have a failed build you should probably delete and re-extract the source, I'm not sure a 'make clean' or make 'distclean' worked properly

If you get a osc error then search out or with a fresh source configure w/

./configure --disable-OSC 

There also is probably a ppa for LiVES or you could install one from getdeb
( new build as of fri. - if so make sure you get proper one for release of ubnutu you're on

[http://www.getdeb.net/](http://www.getdeb.net/)

---

