---
title: "Trying to build CARMEN, libgdk_imlib.a... not found"
date: 2010-02-26
forum: General Help
---

### Post by borntofish61 on 2010-02-26
I'm trying to build sourceforge CARMEN with ubnutu, but get this error(s)

user@ubuntu:~/Carmen/carmen-0.7.4-beta/src$ ./configure
Using $CC as gcc...
Found processor i686.
Congratulations. You are running Linux.
Found kernel 2.6.31-14-generic.
This doesn't look like SuSE!
Searching for linux kernel headers... found at /usr/src/linux-headers-2.6.31-14-generic/include
Searching for canlib... 
Could not find Kvaser canlib header file. I looked for
/usr/include/canlib.h
but it does not seem to exist.

Searching for GTK... found, version 2.18.3
Searching for libgdk_imlib.a... not found 

Could not find libgdk_imlib.a in /usr/lib,
/usr/local/lib, nor in /opt/gnome/lib/
Please install libgdk_imlib.a or
re-run ./configure with --nographics

user@ubuntu:~/Carmen/carmen-0.7.4-beta/src$ apt-file search libgdk_imlib.a
user@ubuntu:~/Carmen/carmen-0.7.4-beta/src$ apt-file search /usr/include/canlib.h
user@ubuntu:~/Carmen/carmen-0.7.4-beta/src$ sudo apt-file search /usr/include/canlib.h
user@ubuntu:~/Carmen/carmen-0.7.4-beta/src$ 

I found this thread, 
[http://ubuntuforums.org/showthread.php?t=1339521]("http://http://ubuntuforums.org/showthread.php?t=1339521")
installed apt-file, but still could not find  libgdk_imlib.a
Guess I could run the ./configure with --nographics, but thoughtI would ask for advice.

Fairly new at this,
Your help is appreciated,
Paul

---

### Post by MiguelS. on 2010-04-07
Hi there,

I think I've found something that may work. Beware though, it's a hack!!

All you have to do is modify the configure script that comes with carmen, simply comment out lines 294 to 286 (which is where the script is cheking whether you have the library installed). You still need the development package for gtk+2 though. I haven't tested exhaustively compiled binaries, but they seem to be ok.

I've also used this to sort a few other compilation problems,
[https://wiki.ubuntu.com/carmen]("https://wiki.ubuntu.com/carmen")

Good luck,
Miguel S.

---

