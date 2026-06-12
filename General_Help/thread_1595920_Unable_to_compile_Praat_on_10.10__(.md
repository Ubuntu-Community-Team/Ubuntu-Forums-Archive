---
title: "Unable to compile Praat on 10.10 : ("
date: 2010-10-13
forum: General Help
---

### Post by Slowey_Joey on 2010-10-13
Hi everyone!

I've been trying to compile a programme from source code on Ubuntu 10.10 but it doesn't seem to working. I am really new to all this, but I have previously compiled it on 10.04 without any problems. It concerns a phonetic analysis programme called Praat ([http://www.fon.hum.uva.nl/praat/download_sources.html](http://www.fon.hum.uva.nl/praat/download_sources.html)).

I have installed build-essentials, and the necessary dependencies listed on the Praat website. When I try to *make,* I basically get a list of things not working. This is the last part of the output - there was a lot more [INDENT]gcc -std=gnu99 -DUNIX -Dlinux -D_REENTRANT -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wimplicit -Wreturn-type -Wunused -Wunused-parameter -Wuninitialized -O -I ../num -I ../sys -I ../dwsys -I ../kar -I ../audio -I ../audio/FLAC -I ../audio/mp3   -c -o melder.o melder.c
In file included from /usr/include/gtk-2.0/gdk/gdkcairo.h:28,
                 from /usr/include/gtk-2.0/gdk/gdk.h:33,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from Gui.h:65,
                 from melder.c:70:
/usr/include/gtk-2.0/gdk/gdkpixbuf.h:37: fatal error: gdk-pixbuf/gdk-pixbuf.h: No such file or directory
compilation terminated.
make[1]: *** [melder.o] Error 1
make[1]: Leaving directory `/usr/local/src/sources_5144/sys'
make: *** [all] Error 2

[/INDENT]I tried installing pixbuf etc. and some other possible solutions without any effect. Like I said, I'm pretty new to all this. 

I appreciate all the help you could give me!


Joey

---

### Post by digital-daniel on 2011-06-19
Did you make any progress with this?

---

### Post by Slowey_Joey on 2011-06-19
Nope, unfortunately I never did.

I ended up simply using the executable downloaded from the website ([http://www.fon.hum.uva.nl/praat/download_linux.html](http://www.fon.hum.uva.nl/praat/download_linux.html)) which worked fine (enough). 

JL

---

### Post by blackmail on 2011-06-19
besides build-essential there are some more dependencies, have a look [here]("http://packages.ubuntu.com/source/lucid/praat")

To install these just type:
```
sudo apt-get install [desired_library-dev]
```

In our case:
```
sudo apt-get install lesstif2-dev
```
 and so on...

Hope with these files you will be able to get it installed, also i executed a search in my software center Ubuntu 11.04 and found that it is there so try:
```
sudo apt-get install praat
```

And also give a visit [here]("http://packages.debian.org/unstable/science/praat") for the .deb package

---

### Post by Slowey_Joey on 2011-06-19
I remember installing lesstif2 without any success. 

Also the package in Synaptic and the .deb concern older versions of the software than the now 5.2.26, although they probably would work.

I never tried compiling it on 11.04, so your solution might work for you, but didn't for me on 10.10

---

### Post by blackmail on 2011-07-22
Fair enough, but make the upgrade, the 11.04 interface is pretty nifty, and also it works better, I have had problems with my guitar recording tool and now it just works out of the box. But if you don't want to update then it is your choice but sadly i can't offer any better solutions since for ma it has worked.

Please post a reply if the problem still persists and if you want to do the upgrade.

Regards

---

