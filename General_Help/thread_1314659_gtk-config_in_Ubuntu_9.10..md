---
title: "gtk-config in Ubuntu 9.10."
date: 2009-11-04
forum: General Help
---

### Post by ednso on 2009-11-04
Hello,

I used to compile Gsview in Jaunty, but I cannot do it in Karmic. The problem is that "gtk-config" is missing. As instance, when I run "make" in in the Gsview compilation folder, I get:
```

make
gcc -O -Wall -Wstrict-prototypes -Wmissing-declarations -Wmissing-prototypes -fno-builtin -fno-common -Wcast-qual -Wwrite-strings -g -DX11 -DUNIX -DNONAG  `gtk-config --cflags`  -DMULTITHREAD -I. -I./src -I./srcunx -I./obj -o ./obj/gvcmisc.o -c ./src/gvcmisc.c
/bin/sh: gtk-config: not found
...

```In Jaunty, when I used to run "gtk-config" the system used to return the package to be installed, but in Karmic I got:
```

ednilton@edlap:~/Desktop/gsview-4.9$ gtk-config
No command 'gtk-config' found, did you mean:
 Command 'gts-config' from package 'libgts-bin' (universe)
gtk-config: command not found

```I searched in Google some time and I found that maybe I should install the package "libgtk2.0-dev". I Installed it and all its dependencies, but "gtk-config" is still missing! :(

So, any idea how I got "gtk-config" file?

Bye.

---

### Post by mc4man on 2009-11-04
gtk-config is only in the 1.X (1.2) version which is no longer in the repos for karmic.

Whether it can be used in karmic haven't had any reason to try.

can be last seen here
[http://packages.ubuntu.com/jaunty/libgtk1.2-dev/filelist](http://packages.ubuntu.com/jaunty/libgtk1.2-dev/filelist)

---

