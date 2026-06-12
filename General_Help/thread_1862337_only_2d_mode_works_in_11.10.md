---
title: "only 2d mode works in 11.10"
date: 2011-10-16
forum: General Help
---

### Post by NattyNoobCake on 2011-10-16
i upgraded to 11.10 when it told me to upgrade from 11.04 
at the end, it said the upgrade was successful but some parts failed. When i try to log in to 11.10, i only see a compiz window (no window borders, no launcher). 11.10 2D mode works though but it doesn't have that many features :(

---

### Post by NattyNoobCake on 2011-10-16
bump

---

### Post by Gitominoti on 2011-10-16
I'm assuming it's because of your Compiz settings. Is Unity enabled in the Compiz manager?

---

### Post by gufide on 2011-10-16
try this, if you pass the test, then unity 3d should work
just type this in the terminal:
```
/usr/lib/nux/unity_support_test -p
```

and paste the output in a post

---

### Post by NattyNoobCake on 2011-10-20
> **gufide said:**
> try this, if you pass the test, then unity 3d should work
just type this in the terminal:
```
/usr/lib/nux/unity_support_test -p
```

and paste the output in a post

```
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 
OpenGL version string:  2.1 Mesa 7.11

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

tried it, still doesn't work

---

