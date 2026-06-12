---
title: "Compile problem"
date: 2005-02-23
forum: General Help
---

### Post by apokryphos on 2005-02-23
On trying to compile a package, I get the following error in the make:

> sr/share/qt3/lib -L/usr/X11R6/lib    -module -avoid-version -no-undefined -Wl,--no-undefined -Wl,--allow-shlib-undefined  main.lo memory.lo opengl.lo  -lkdeui      -lGLU -lGL -lX11 
/usr/lib/libGL.a(glxcmds.o)(.text+0x2eea): In function `glXGetMscRateOML': 
: undefined reference to `XF86VidModeQueryVersion' 
/usr/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function `glXGetMscRateOML': 
: undefined reference to `XF86VidModeGetModeLine' 
collect2: ld returned 1 exit status 
make[3]: *** [kcm_info.la] Error 1 
After a bit of searching and asking on the IRC, someone found this webpage talking about one of the errors: [http://www.xfree86.org/4.0.1/XF86VidMode.3.html](http://www.xfree86.org/4.0.1/XF86VidMode.3.html)

However, what I find odd is that article there speaks of XFree, and I've got a fully functioning xorg (didn't install it too long ago... had some hassle but all resolved). Anyone got any ideas here? The package certainly doesn't need Xfree to install.

---

