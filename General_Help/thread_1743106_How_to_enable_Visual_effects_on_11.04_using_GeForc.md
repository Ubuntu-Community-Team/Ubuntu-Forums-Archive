---
title: "How to enable Visual effects on 11.04 using GeForce 9300"
date: 2011-04-29
forum: General Help
---

### Post by moyajaya on 2011-04-29
Hello! 

As the title says, I have just installed ubuntu 11.01 and I'd like to enable the visual effects. I have a touchsmart 600 

Running this:
```
lspci | grep VGA
```

Results on this:
```
jaya@jaya-ubuntu:~$ lspci | grep VGA
03:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9300] (rev b1)
```


and running this:
```
/usr/lib/nux/unity_support_test -p
```

Results on this:
```
jaya@jaya-ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce G200/PCI/SSE2
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


Thank you in advance!

---

### Post by dino99 on 2011-04-29
unity load compiz by default, nothing to do

---

### Post by moyajaya on 2011-04-29
Thank you for your response dino99, 

I don't have the option to enable visual effects under appearance and thus I can't benefit from the extra visual effects like minimize animation and flexible windows when moving them around..

---

### Post by 3Miro on 2011-04-29
If you are using Unity, you are running visual effects.

If you want to configure individual effects (turn stuff on or off, key-binding and so on), then you should install CCSM (compiz-config-setting-manager) form the Software Center.

---

### Post by moyajaya on 2011-04-29
thank you very much! Installed it and customized things to my needs. 

Have a great day!

---

### Post by kikoalemao on 2011-04-29
Mine is :
```
:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)

```-
```
:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 7.10.2

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

```I also don't see advanced visual effects or enable it in Appearance, as I could do in <10.10 . Was it really taken off to be managed only in compiz? 
Another strange behaviour was to see 5 of the options in "Working Environment" at Keyboard Shortcut with both Action and Shortcut set to "Unknown". Could not find what each of them is related to.
Anyone have a clue?

---

