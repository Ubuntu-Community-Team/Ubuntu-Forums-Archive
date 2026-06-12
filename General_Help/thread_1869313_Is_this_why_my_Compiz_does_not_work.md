---
title: "Is this why my Compiz does not work?"
date: 2011-10-25
forum: General Help
---

### Post by atentik on 2011-10-25
Well, it seem my compiz does not work, even after enabling it. I used to press Alt+Ctrl+ TAB to select screens in an impressive fashion but now after upgrading to Ubuntu 11.10, this does not work anymore, not even in unity-2d. Even Cairo-dock does not work properly.
Here is my ```
/usr/lib/nux/unity_support_test -p

```
[PHP]OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.11

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
[/PHP]
It says, I am using the "Mesa" project, should that not be intel since my
```
lspci | grep VGA
```
produces
[PHP]00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
[/PHP] if so, how do I change it reflect the exact OpenGL or are they completely two different things altogether. 

Also, how do I get it to render softer? 

Thanks

---

