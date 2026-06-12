---
title: "Trying To Scon ROX Applet"
date: 2009-12-05
forum: General Help
---

### Post by Mark76 on 2009-12-05
And I keep getting this

> scons: Reading SConscript files ...
Checking for C library X11... yes
Checking for C header file X11/Xatom.h... yes
Package gdu was not found in the pkg-config search path.
Perhaps you should add the directory containing `gdu.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gdu' found
OSError: 'pkg-config --cflags --libs gconf-2.0 gdu gtk+-2.0 gdk-pixbuf-2.0' exited 1:
  File "/home/mark/Apps/ROX-Media/SConstruct", line 1:
    SConscript('src/SConscript')
  File "/usr/lib/scons/SCons/Script/SConscript.py", line 612:
    return apply(method, args, kw)
  File "/usr/lib/scons/SCons/Script/SConscript.py", line 549:
    return apply(_SConscript, [self.fs,] + files, subst_kw)
  File "/usr/lib/scons/SCons/Script/SConscript.py", line 259:
    exec _file_ in call_stack[-1].globals
  File "/home/mark/Apps/ROX-Media/src/SConscript", line 22:
    media_env.ParseConfig('pkg-config --cflags --libs ' \
  File "/usr/lib/scons/SCons/Environment.py", line 1447:
    return function(self, self.backtick(command))
  File "/usr/lib/scons/SCons/Environment.py", line 585:
    raise OSError("'%s' exited %d" % (command, status))
rox-media compile failed.
Press Return to continue...



Where have you hidden gdu?

---

### Post by endBc on 2009-12-05
[http://packages.ubuntu.com/search?keywords=gdu&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=gdu&searchon=names&suite=karmic&section=all) - no one have hided it anywhere :)

---

### Post by Mark76 on 2009-12-05
If only there weren't so many broken dependencies

---

### Post by endBc on 2009-12-05
> **Mark76 said:**
> If only there weren't so many broken dependencies

There are no broken dependencies in your screenshot. Does searching for it from command line return 0 results, too ?

---

### Post by Mark76 on 2009-12-05
I was talking about the dependencies when I try to install from the Ubuntu debs

---

### Post by endBc on 2009-12-05
Missing isn't the same as broken. Anyway, I think it'll be easier to figure out why you can't install them with Aptitude rather than download them manually.

---

### Post by Mark76 on 2009-12-05
Why can't I find the damned thing in Synaptic?

---

