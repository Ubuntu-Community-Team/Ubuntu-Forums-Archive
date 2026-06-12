---
title: "Aiglx libGL warning"
date: 2006-06-14
forum: General Help
---

### Post by leohart on 2006-06-14
Hi guys,

I followed the instructions on Compiz + Aiglx thread and successfully get Compiz and Aiglx working. 

There is a slight problem however. When I try running several softwares such as IE6 (through wine), Google Earth, glxgears, the console will output something similar to the below

```
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
```

Those softwares would not work perfectly either. Is this a driver issue and how do I fix it?

I am running on a stock Inspiron 6000 with Intel i915

---

### Post by lalborno on 2006-06-14
leohart,

I have the same error when i run a screensaver like glmatrix:

```
$ /usr/lib/xscreensaver/glmatrix
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32

```

this opens the glmatrix screensaver on a window (and it looks fine, not flickering or slow or anithing), but the content of the window looks always on top, and it does not support transparency, scale, rotate or zoom. 

It looks like if the glmatrix is bypassing compiz, even when other applications work fine and compiz does not have any trouble applying the pugins on them, like on firefox, terminal and so on.


I had the same problem with vlc media player but i solved setting X11 Video Output instead of the default. 

Anyone knows how to solve this? Please? :sad:

---

