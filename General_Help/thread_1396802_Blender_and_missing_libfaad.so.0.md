---
title: "Blender and missing libfaad.so.0"
date: 2010-02-02
forum: General Help
---

### Post by bobnutfield on 2010-02-02
Hello Everyone,

In installed Blender from the repos to learn 3D modeling in an attempt to use it for jewellery design.  However, it won't open because it is looking for libfaad.so.0 and can't find it.  I have faad installed, but I believe it is a newer version than the one Blender is looking for (libfaad.so.2)

Anyone know a workaround for this?  Any thoughts greatly appreciated.

Bob

---

### Post by rnerwein on 2010-02-02
hi - i found this in ubuntu posts (it's marked solved)

 ffmpeg errors with libfaad.so.0
 Ran into a problem:
 $ ffmpeg
 ffmpeg: error while loading shared libraries: libfaad.so.0: cannot open shared object file: No such file or directory

 Diagnosis:
 This is due to a library provided by faad2 package. Karmic provides version 2.6.1 which is actually quite old. If you have installed faad 2.7.X, then you will experience this problem.

 Solution (stable but with old version):
 Start synaptic, search for package faad2, force version 2.6.1 and everything works.

 Solution (new but untested)::

may be it will help you
ciao

---

### Post by cotcot on 2010-05-13
Same problem with lucid after the official release.

A work around is to download the binary from the blender site, extract it, go to the extracted folder and start blender with the executable in this extracted folder.

---

### Post by clwade on 2011-01-12
> **rnerwein said:**
> hi - i found this in ubuntu posts (it's marked solved)

 ffmpeg errors with libfaad.so.0
 Ran into a problem:
 $ ffmpeg
 ffmpeg: error while loading shared libraries: libfaad.so.0: cannot open shared object file: No such file or directory

 Diagnosis:
 This is due to a library provided by faad2 package. Karmic provides version 2.6.1 which is actually quite old. If you have installed faad 2.7.X, then you will experience this problem.

 Solution (stable but with old version):
 Start synaptic, search for package faad2, force version 2.6.1 and everything works.

 Solution (new but untested)::

may be it will help you
ciao

I solved this with a symbolic link to the existing library - works for ffmpeg, can't speak to other applications:

ls -l /usr/lib/libfaad*
-rw-r--r-- 1 root root 293596 2009-11-09 23:26 libfaad.a
lrwxrwxrwx 1 root root     16 2011-01-11 17:05 libfaad.so -> libfaad.so.2.0.0
lrwxrwxrwx 1 root root     16 2011-01-11 20:08 libfaad.so.0 -> libfaad.so.2.0.0
lrwxrwxrwx 1 root root     16 2010-05-19 08:08 libfaad.so.2 -> libfaad.so.2.0.0
-rw-r--r-- 1 root root 255300 2009-11-09 23:26 libfaad.so.2.0.0

---

