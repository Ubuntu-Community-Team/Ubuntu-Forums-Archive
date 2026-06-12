---
title: "Dependency problem with 'gtk+-2.0' (I do have libgtk2.0-dev)"
date: 2009-12-28
forum: General Help
---

### Post by agnes on 2009-12-28
I was trying to install wxcam 1.0.4 from source (on AMD64, in dir. /usr/local/bin) it says, when running ./configure:
```
checking for WXCAM... configure: error: Package requirements (gtk+-2.0 libglade-2.0 mjpegtools) were not met:

No package 'gtk+-2.0' found
No package 'libglade-2.0' found
No package 'mjpegtools' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables WXCAM_CFLAGS
and WXCAM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

But I do have libgtk2.0-dev:
```
$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-dev is already the newest version.

```
Also installed is libgtk-directfb-2.0-dev.
And the the mjpegtools and libglade2-dev. So I guess the problem is solely with the gtk+2.0 thing.

I don't know about the "WXCAM"-variables but I've set PKG_CONFIG like this in my .bashrc:
```
$ echo $PKG_CONFIG_PATH
/usr/lib/pkgconfig
```
Which should be right because:
```
$ ls /usr/lib | grep pkg
dpkg
libapt-pkg-libc6.8-6.so.4.6
libapt-pkg-libc6.8-6.so.4.6.0
pkgconfig
$ dpkg-query -S gtk+-2.0
libgtk2.0-dev: /usr/lib/pkgconfig/gtk+-2.0.pc
```

So what can this be?!

---

### Post by agnes on 2009-12-28
Ok I just installed the newest i386 package using 

$ sudo dpkg -i --force-architecture wxcam*.deb
and
$ getlibs /usr/bin/wxcam

Maybe a tip for people having the same issue.
Of course this is not ideal, now I'm having 4 extra i386 libraries. :-&

---

