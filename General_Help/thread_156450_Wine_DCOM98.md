---
title: "Wine DCOM98"
date: 2006-04-07
forum: General Help
---

### Post by Fatstink on 2006-04-07
when I try to load the DCOM 98 it fails on me and gives me an error.

1229056 bytes previously downloaded
WINEDEBUG="fixme-all" WINEDLLOVERRIDES="ole32=n" wine ./dcom98.exe
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
waiting for wineservers to exit...

Where can I get the libXxf86dga file to open this??? or does anyone know of a different way to fix this???

---

### Post by mlind on 2006-04-07
do you have package called *libxxf86dga1* installed?
you may need *libxxf86dga1-dev* aswell.

---

### Post by Fatstink on 2006-04-07
I have the package, should I go get the dev for them as well?

---

### Post by Fatstink on 2006-04-08
Is there any place I can get a good DCOM98???

---

### Post by mlind on 2006-04-08
[QUOTE=Fatstink]Is there any place I can get a good DCOM98???[/QUOTE]

it's a microsoft component, so from m$ site probably. have you checked out
automatic install scripts like  [WineTools]("http://www.von-thadden.de/Joachim/WineTools/") yet?
It installs DCOM98 and IE6 for you automatically.

---

### Post by Fatstink on 2006-04-08
That is where I get the error message from.  I was thinking I just had a bad copy of the DCOM98.  But I am now thinking it has something to do with my AMD64

---

### Post by usergentoo on 2006-04-08
Its not you I have on my desktop a older version of wine and everything works great. On my laptop installed the newset version today and nothing works. DCOM98 is broken IE6 nolonger works. Even tried the deb from the wine repo and no luck with it either. It seems they broke something with this newer version.

---

### Post by Fatstink on 2006-04-09
so do I just install an older version or wait until the bugs are fixed???

---

