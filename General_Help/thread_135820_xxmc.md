---
title: "xxmc"
date: 2006-02-24
forum: General Help
---

### Post by Rizado on 2006-02-24
I'm trying to get XvMC working with my Nvidia 6600GT, It's not going to well...

What I'm trying to do is compiling xine-lib (And later kaffeine too) with xxmc support but it just wont work. Here's something from ./configure

```
checking for libXv.so... found libXv.so in /usr/X11R6/lib
checking for XvShmCreateImage in -lXv... yes
checking whether to enable the xxmc plugin with vld extensions...
checking for XvMCPutSlice in -lXvMCW... no
*** Could not link with -lXvMCW for vld extensions.
checking for XvMCCreateContext in -lXvMCW... no
*** Could not link with -lXvMCW for standard XvMC.
*** Disabling xxmc plugin due to above errors.
checking whether to enable the xvmc plugin...
checking for XvMCCreateContext in -lXvMCW... (cached) no
*** Could not link with -lXvMCW.
*** Disabling old xvmc plugin due to above errors.
```I have made a link called libXv.so in /usr/X11R6/lib, otherwise it couldn't find it. I've created /etc/X11/XvMCConfig with only one line in it: libXvMCNVIDIA.so.1.0.8178. Of course I have nvidia 8178 drivers too. I have installed libxvmc through apt and I've also run sudo ldconfig. What else is there to do?

I'm sorry if it's hard to follow, or If i've missed something. I'm just really tired right now.

---

### Post by Rizado on 2006-02-25
Well, I knew I was gonna work it out after some sleep.
Here's a link to something: [http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=281572](http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=281572)
And here's the link to libXvMCW: [http://www.physik.fu-berlin.de/~glaweh/debian/](http://www.physik.fu-berlin.de/~glaweh/debian/)

If anyone need help with this just ask.

---

