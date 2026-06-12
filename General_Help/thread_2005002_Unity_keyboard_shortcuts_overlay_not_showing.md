---
title: "Unity keyboard shortcuts overlay not showing"
date: 2012-06-16
forum: General Help
---

### Post by RKB101 on 2012-06-16
Hi,

New to Ubuntu, loving it so far, anyway when I hold down the windows key the shortcuts overlay doesn't appear, only numbers on top of my launcher icons.

Thanks

---

### Post by vasa1 on 2012-06-16
This happens, IMO, if Unity 2D is running:
[http://ubuntuforums.org/showpost.php?p=11917734&postcount=10](http://ubuntuforums.org/showpost.php?p=11917734&postcount=10)
and
[http://ubuntuforums.org/showpost.php?p=11919376&postcount=14](http://ubuntuforums.org/showpost.php?p=11919376&postcount=14)

To know if Unity is in 2D mode, run this code in a terminal (accessed by typing control+alt+t together):
```
/usr/lib/nux/unity_support_test -p
```

You should see output like```
 /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 8.0.2

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

### Post by RKB101 on 2012-06-17
This is my output: 

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) IGD x86/MMX/SSE2
OpenGL version string:  1.4 Mesa 8.0.2

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

---

### Post by kostkon on 2012-06-17
what is your resolution. The overlay will not appear in resolutions 1204x600 or lower.

---

### Post by RKB101 on 2012-06-17
> **kostkon said:**
> what is your resolution. The overlay will not appear in resolutions 1204x600 or lower.

That must be the problem, my resolution is 1024 x 600. Are all the shortcuts displayed under keyboard > shortcuts?

---

### Post by kostkon on 2012-06-17
For a list of all the available shortcuts in 12.04 see [here]("http://askubuntu.com/questions/28086/what-are-unitys-keyboard-and-mouse-shortcuts").

---

### Post by RKB101 on 2012-06-17
Thanks :) how would you change the resolution of the display (other than by system preferences > displays)

---

### Post by vasa1 on 2012-06-17
> **kostkon said:**
> what is your resolution. The overlay will not appear in resolutions 1204x600 or lower.
Very interesting! Where is reference to this limitation to be found? It's not here: [Keyboard shortcut - Add keyboard shortcut hint overlay that is displayed when a user presses and holds the Super key]("https://bugs.launchpad.net/ayatana-design/+bug/855532")

---

### Post by kostkon on 2012-06-17
> **vasa1 said:**
> Very interesting! Where is reference to this limitation to be found? It's not here: [Keyboard shortcut - Add keyboard shortcut hint overlay that is displayed when a user presses and holds the Super key]("https://bugs.launchpad.net/ayatana-design/+bug/855532")
See the [bug report]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/922979").

---

### Post by vasa1 on 2012-06-17
> **kostkon said:**
> See the [bug report]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/922979").

Thanks for that. It doesn't affect me but that bug doesn't make for pleasant reading.

---

