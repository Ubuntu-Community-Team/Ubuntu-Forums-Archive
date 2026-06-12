---
title: "reinstalling main files"
date: 2006-04-22
forum: General Help
---

### Post by sunrex on 2006-04-22
i seem to have deleted this file "error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory"

so how do i reinstall the main files without deleting the files already on my os..

---

### Post by cilynx on 2006-04-22
```

apt-get install --reinstall [package]

```

libGL.so.1 can be sourced from quite a few packages...it depends on what you have installed

```

rcw@pyth:~$ apt-file search libGL.so.1
libgl1-mesa: usr/lib/libGL.so.1
libgl1-mesa: usr/lib/libGL.so.1.2
libgl1-mesa-glide3: usr/lib/i686/mmx/cmov/libGL.so.1
libgl1-mesa-glide3: usr/lib/i686/mmx/cmov/libGL.so.1.5.060201
libgl1-mesa-glide3: usr/lib/libGL.so.1
libgl1-mesa-glide3: usr/lib/libGL.so.1.5.060201
libgl1-mesa-swrast: usr/lib/i686/mmx/cmov/libGL.so.1
libgl1-mesa-swrast: usr/lib/i686/mmx/cmov/libGL.so.1.5.060401
libgl1-mesa-swrast: usr/lib/libGL.so.1
libgl1-mesa-swrast: usr/lib/libGL.so.1.5.060401
libgl1-mesa-swrast-dbg: usr/lib/debug/i686/mmx/cmov/libGL.so.1
libgl1-mesa-swrast-dbg: usr/lib/debug/i686/mmx/cmov/libGL.so.1.5.060401
libgl1-mesa-swrast-dbg: usr/lib/debug/libGL.so.1
libgl1-mesa-swrast-dbg: usr/lib/debug/libGL.so.1.5.060401
nvidia-glx: usr/lib/libGL.so.1
nvidia-glx: usr/lib/libGL.so.1.0.8178
nvidia-glx-legacy: usr/lib/libGL.so.1
nvidia-glx-legacy: usr/lib/libGL.so.1.0.7174
xorg-driver-fglrx: usr/lib/libGL.so.1
xorg-driver-fglrx: usr/lib/libGL.so.1.2
rcw@pyth:~$

```

---

