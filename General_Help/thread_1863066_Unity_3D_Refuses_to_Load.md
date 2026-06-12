---
title: "Unity 3D Refuses to Load"
date: 2011-10-17
forum: General Help
---

### Post by Joshwaa on 2011-10-17
Here's my problem:
I'm running Ubuntu 11.10 and all I've been doing for the past few days is trying to make stuff work.
My latest problem is with Unity 3D (which is probably caused by my Nvidia graphics card - Ubuntu seems to hate Nvidia from what I've experienced).

Unity doesn't load upon login with Unity 3D whereas Unity 2D will work fine.

Any suggestions?

---

### Post by gandaran on 2011-10-17
did you install nvidia drivers from additional drivers?
or post the video card specifications.

---

### Post by Joshwaa on 2011-10-17
> **gandaran said:**
> did you install nvidia drivers from additional drivers?
or post the video card specifications.

Yeah I did, I also reinstalled nvidia-current and nvidia-settings from the Terminal and no luck.
I'm using a Nvidia Geforce G210M 512MB

---

### Post by gandaran on 2011-10-17
run this test and paste the output
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by Joshwaa on 2011-10-17
> **gandaran said:**
> run this test and paste the output
```
/usr/lib/nux/unity_support_test -p
```

```
Error: OpenGL rendering is not supported by the root visual

```

---

### Post by Joshwaa on 2011-10-17
> **gandaran said:**
> run this test and paste the output
```
/usr/lib/nux/unity_support_test -p
```

After reinstalling the Nvidia drivers here's what I get:
(Note: Unity 3D still doesn't work)

```
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce G210M/PCI/SSE2
OpenGL version string:  3.3.0 NVIDIA 285.05.09

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

---

### Post by gandaran on 2011-10-17
try the nvidia drivers from this PPA
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
add the PPA to software sources and update the software package list then check if nvidia update is available for install.

---

### Post by Joshwaa on 2011-10-17
> **gandaran said:**
> try the nvidia drivers from this PPA
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
add the PPA to software sources and update the software package list then check if nvidia update is available for install.

I've managed to figure out that's its JUST on MY user account that Unity 3D won't work.. I'm confused

---

### Post by pa3fat on 2011-10-17
Not trying to steal this thead but have similar issue. Although my output from the command is different:

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Desktop GEM 20100330 DEVELOPMENT x86/MMX/SSE2
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



It doesn'teven mention that 3D is supported. CPU is a G620T Sandybridge type.
Would have expected it could do a bit more.

Again not trying to take over. Please advise if i need to raise another thread for my specific situation.

Found that G620T is not supporting 3D on Intel website. Carry on :)

---

### Post by pactel on 2011-10-17
> **Joshwaa said:**
> I've managed to figure out that's its JUST on MY user account that Unity 3D won't work.. I'm confused

Try the solution in this thread. Worked for me, having the same problem.

[http://ubuntuforums.org/showthread.php?t=1862375]("http://ubuntuforums.org/showthread.php?t=1862375")

Basically empty the file; ~/.config/compiz-1/compizconfig/config

---

