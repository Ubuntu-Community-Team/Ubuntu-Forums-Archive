---
title: "Realvnc got error loading lib: libstdc++-libc6.2-2.so.3: &lt;no file&gt;"
date: 2011-12-20
forum: General Help
---

### Post by rhb on 2011-12-20
Hello,

    I installed Realvnc to share a desktop with an M$ machine.  I have an odd library name that seems to be missing --

vncpasswd: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

   I am running 10.10 64 bit, installed via wubi.  I googled, got recommendation to load a 2.10 version, which doesn't exist, then the idea that it's a compat package that's needed, but I can't track it down.  Is that really the name of a single library?  Are they dependent on an old version of something?    It is obviously a 32-bit app since it claims to work on both.

    Here is the full script output.  It is GPL'ed, but I think it's mainly a teaser for their proprietary package.

..tu:/media/downloads/progs/linux/vnc-4_1_3-x86_linux$ sudo ./vncinstall /usr/local/bin /usr/local/man
Copying Xvnc to /usr/local/bin
Copying Xvnc.man to /usr/local/man/man1/Xvnc.1
Copying vncviewer to /usr/local/bin
Copying vncviewer.man to /usr/local/man/man1/vncviewer.1
Copying vncpasswd to /usr/local/bin
Copying vncpasswd.man to /usr/local/man/man1/vncpasswd.1
Copying vncconfig to /usr/local/bin
Copying vncconfig.man to /usr/local/man/man1/vncconfig.1
Copying vncserver to /usr/local/bin
Copying vncserver.man to /usr/local/man/man1/vncserver.1
Copying x0vncserver to /usr/local/bin
Copying x0vncserver.man to /usr/local/man/man1/x0vncserver.1
..tu:/media/downloads/progs/linux/vnc-4_1_3-x86_linux$ vncserver

You will require a password to access your desktops.

vncpasswd: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
rhb@ubuntu:/media/downloads/progs/linux/vnc-4_1_3-x86_linux$ sudo apt-get install libstdc++2.10-glibc2.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libstdc++2.10-glibc2.2
E: Couldn't find any package by regex 'libstdc++2.10-glibc2.2'
rhb@ubuntu:/media/downloads/progs/linux/vnc-4_1_3-x86_linux$

---

### Post by fragos on 2011-12-20
Looks like somehow two library names were concatenated together. There are libs with libstdc++ and libc6 in their names but they are separate libs. At least this is the case on a 32bit install.

---

### Post by rhb on 2011-12-21
I learned a little more about it.  The name apparently needs to be linked to the appropriate version of libstdc++.  My understanding is that the name used means "the libstdc++ which goes with libc6.2-2.so.3".  This is an old problem, and it appears the library it needs came with feisty or edgy and is no longer available.

It turns out that tsclient, which I also tried to use, has the same problem.  My guess is that realvnc modified that version slightly for their free version.  Probably tsclient should either be fixed or else be removed from the current package list or at least marked 'not recommended'.

I tried again with vinagre and it seems to work at least as far as being able to connect to my own desk top.  For now I will forget about trying to use the same program as my contact, unless I can convince him to install vinagre.

---

### Post by fragos on 2011-12-21
vinagre is what I use on my LAN, it's the default vnc viewer. There's another VNC package that's very popular called Remmina that's in the software center. In the past I used xtightvncviewer. They have their differences but for my purposes are all pretty much interchangeable.

---

