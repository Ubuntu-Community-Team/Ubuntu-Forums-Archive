---
title: "What vid driver am I running?"
date: 2011-05-17
forum: General Help
---

### Post by stinkeye on 2011-05-17
In Natty, Jockey shows me that the current nvidia driver is
Activated but **not** currently in use.

nvidia-settings shows 
NVIDIA Driver Version:270.41.06

It appears to me that the nvidia driver is in use as I upgraded from version 173 
to the current version and performance improved.
Is this a jockey-gtk bug?

```
glen@Natty:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9400 GT/PCI/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 270.41.06

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

Unity supported:          yes
```

---

### Post by wildmanne39 on 2011-05-17
> **stinkeye said:**
> In Natty, Jockey shows me that the current nvidia driver is
Activated but **not** currently in use.

nvidia-settings shows 
NVIDIA Driver Version:270.41.06

It appears to me that the nvidia driver is in use as I upgraded from version 173 
to the current version and performance improved.
Is this a jockey-gtk bug?

```
glen@Natty:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9400 GT/PCI/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 270.41.06

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

Unity supported:          yes
```
Hi,yes there is a bug that shows the driver is not being used but the one you activated is actually being used.

---

### Post by stinkeye on 2011-05-17
Thanks.

---

### Post by wildmanne39 on 2011-05-17
> **stinkeye said:**
> Thanks.

Hi, your welcome.

---

