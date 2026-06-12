---
title: "trying to compile audacity"
date: 2009-08-18
forum: General Help
---

### Post by shiggydiggy on 2009-08-18
I installed wx-widgets, but i still get this when i go ./configure
```

checking for zip... /usr/bin/zip
checking for wx-config... no
configure: error: "Could not find wx-config: is wxWidgets installed? is wx-config in your path?"

```when i type wx-config i get this
```

stanley@stanley-desktop:~/stuffs/audacity-src-1.2.6$ wx-config
The program 'wx-config' can be found in the following packages:
 * libwxbase2.4-dbg
 * libwxbase2.4-dev
 * libwxbase2.6-dbg
 * libwxbase2.6-dev
 * libwxbase2.8-dbg
 * libwxbase2.8-dev
 * libwxgtk2.4-dbg
 * libwxgtk2.4-dev
 * libwxgtk2.6-dbg
 * libwxgtk2.6-dev
 * libwxgtk2.8-dbg
 * libwxgtk2.8-dev
Try: sudo apt-get install <selected package>
bash: wx-config: command not found

```

---

### Post by Yellow Pasque on 2009-08-18
```
sudo apt-get install libwxgtk2.8-dev
```
In fact, you can make life easier by:
```
sudo apt-get build-dep audacity
```

---

### Post by shiggydiggy on 2009-08-18
> **Temüjin said:**
> ```
sudo apt-get install libwxgtk2.8-dev
```In fact, you can make life easier by:
```
sudo apt-get build-dep audacity
```
I did the latter but when i went ./configure it did this
```

checking for wx-config... /usr/bin/wx-config
configure: Checking that the installed version of wxWidgets is 2.4.x
configure: error: Unable to locate a suitable configuration of wxWidgets v2.4.x.
The currently available configurations are listed below.  If necessary, either
install the package for your distribution or download the 2.4.x version of
wxWidgets from http://wxwidgets.org.
To help configure find the right version set WX_CONFIG to point to it.
wxWidgets 2.5.x and 2.6.x are NOT supported!

```
so i tried
```
sudo apt-get install libwxgtk2.4-dev
```
it installed it but didn't make a difference :(

---

### Post by Yellow Pasque on 2009-08-18
Are you trying to compile an older version? Is there something wrong with the version in the Ubuntu repository?

---

### Post by shiggydiggy on 2009-08-18
yea, the one that comes with ubuntu is a dev version; 1.37. it won't read the FLACs that sound recorder makes, nor the OGGs that VLC makes if I convert my FLACs.

---

### Post by mc4man on 2009-08-18
```
sudo update-alternatives --config wx-config
```
pick the one would like to currently use. ( probably wgtk rather than wxbase

---

### Post by shiggydiggy on 2009-08-18
sweet! got past the ./configure part

when i go 'make' (which is the next step in the readme instructions i get this

```
se_optimized.cpp:313: error: '_mm_add_ps' was not declared in this scope
sse_optimized.cpp:334: error: '_MM_SHUFFLE' was not declared in this scope
sse_optimized.cpp:334: error: '_mm_shuffle_ps' was not declared in this scope
sse_optimized.cpp:336: error: '_mm_add_ps' was not declared in this scope
sse_optimized.cpp:336: error: '_mm_storeu_ps' was not declared in this scope
make[4]: *** [sse_optimized.lo] Error 1
make[4]: Leaving directory `/home/stanley/stuffs/audacity-src-1.2.6/lib-src/soundtouch/source/SoundTouch'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/stanley/stuffs/audacity-src-1.2.6/lib-src/soundtouch/source'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/stanley/stuffs/audacity-src-1.2.6/lib-src/soundtouch'
make[1]: *** [soundtouch/source/SoundTouch/.libs/libSoundTouch.a] Error 2
make[1]: Leaving directory `/home/stanley/stuffs/audacity-src-1.2.6/lib-src'
make: *** [audacity] Error 2

```
that's not all of it... hopefully it gives someone a clue what i need to do.. hey that rhymes!:guitar:

---

### Post by shiggydiggy on 2009-08-22
BUMP!
can i please get some help?

---

