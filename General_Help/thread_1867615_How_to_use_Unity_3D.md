---
title: "How to use Unity 3D?"
date: 2011-10-23
forum: General Help
---

### Post by calande on 2011-10-23
Hello,

I upgraded to 11.10, and when I start my computer, I'm logged into a desktop that only has a top bar with unresponsive menu, and a wall paper. I have to log out and log back into Unity 2D, but I'd like to use 3D. How can I do that? Maybe I need extra configuration? I am using NVIDIA graphics driver 173, and I enabled Unity plugin in ccsm. Thanks if you have any suggestion.

---

### Post by JRV on 2011-10-23
This command will tell you if your hardware will support Unity 3D:

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by calande on 2011-10-23
Thanks, oh, it won't :'(

/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE2/3DNOW!
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

---

### Post by JRV on 2011-10-23
Activate the driver that says "(Recommended)" and see what happens.

---

### Post by haresear on 2011-10-23
I have the Nvidia FX5200 video card, and have tried all the Nvidia 173 drivers from Ubuntu and Nvidia -- Unity 3D just doesn't work with this combo. Gnome shell will run, but is so slow it is unusable.

---

### Post by calande on 2011-10-23
This driver is already active. Thanks.

---

