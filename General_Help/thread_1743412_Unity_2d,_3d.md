---
title: "Unity 2d, 3d?"
date: 2011-04-29
forum: General Help
---

### Post by bazcor on 2011-04-29
I am a little puzzled by this. Using the app to test for video support gives the following result:

barry@natty:~$ /usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTS 250/PCI/SSE2
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

Yet the hardware drivers says 'The Nvidia driver is loaded but not in use'.

The 2d unity desktop is running and the windows effects are working, also the Nvidia control applet is present.

Am I using the restricted Nvidia driver or not?

any input more than welcome... Barry

---

### Post by mc4man on 2011-04-29
Yes nvidia drivers are loaded, I wouldn't pay any attention to what add. drivers says - see the same here on all my installs

If you didn't install unity-2d then can't see how it is running?

What does this show (I updated to the latest unity the other day to test
> $ unity --version
unity 3.8.12

---

### Post by sikander3786 on 2011-04-29
Please post the output of this command.

```
cat /etc/X11/xorg.conf
```

Your graphics card is efficient enough to handle Unity.

---

### Post by bazcor on 2011-04-29
Yes unity 2d is running and your comment makes sense as the graphics are very smooth, (to smooth for noveau I'de say).


barry@natty:~$ unity --version
unity 3.8.10

is what I get .. Thanks for your reply .. Barry

---

### Post by bazcor on 2011-04-29
barry@natty:~$ cat /etc/X11/xorg.conf

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection


Thanks for any further input .. Barry

---

### Post by mc4man on 2011-04-29
> **bazcor said:**
> Yes unity 2d is running and your comment makes sense as the graphics are very smooth, (to smooth for noveau I'de say).


barry@natty:~$ unity --version
unity 3.8.10

is what I get .. Thanks for your reply .. Barry
Then you're running the unity 3d, (compiz based),  not unity-2d (qt4 based

---

### Post by bazcor on 2011-04-29
Thanks for that, I let these things worry me, when I know that the installation seems to be working fine! I'll mark this one as solved I guess. Thanks again .. Barry

---

