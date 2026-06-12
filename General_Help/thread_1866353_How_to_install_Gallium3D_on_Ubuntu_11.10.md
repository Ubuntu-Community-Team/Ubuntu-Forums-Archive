---
title: "How to install Gallium3D on Ubuntu 11.10"
date: 2011-10-21
forum: General Help
---

### Post by emptycoder on 2011-10-21
Hi, I'm still noob, so please bear with me.
I recenetly had some problems with ATI Radeon HD 5470, so I did some researches and I found out about Mesa Gallium3D Driver.
They were so many posts and different insturctions so simply I'm lost!
Would you please guide me how to install Gallium3D step by step please?
And could someone explain me what is xorg-edgers for, in brief?
Thanks a lot!

---

### Post by pme 72 on 2011-10-21
Gallium should be installed by default. You could open a Terminal and run this code. It is for checking if Unity 3D is supported but the line OpenGL renderer string will show Gallium if it is present. 

```
/usr/lib/nux/unity_support_test -p
```

That OpenGL line from the output of my HD4550 shows:

OpenGL renderer string: Gallium 0.4 on AMD RV710

It looks like you have hybrid (switchable) graphics though. Your output will depend on which card is enabled.

---

### Post by castironpants on 2011-11-03
I have the same video card but I can't get Gallium. I've added xorg-edgers and upgraded all my packages 

```
[jeremy:~]$  /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.12-devel

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

---

### Post by pme 72 on 2011-11-03
Do you have hybrid (switchable) graphics?

---

