---
title: "Help with ATI"
date: 2011-12-08
forum: General Help
---

### Post by seojunkim on 2011-12-08
System:
Samsung Sens R60 Plus
Intel Celeron 530M @ 1.73GHz (Single Core)
ATI Radeon X1250 
Phoenix Motherboard
120 GB Harddisk (Samsung)
15.1 inch display
_____________________________________
My graphics card suddenly doesn't support unity. 
It used to support unity, however, one day it suddenly
"transformed" and doesn't support unity anymore if i
do the unity support test.
I used to be able to go into unity now if I go in unity ubuntu
automatically reverts to unity 2d....


seojunkim@seojunkim-R59P-R60P-R61P:~$ /usr/lib/nux/unity_support_test -p  
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

^That is what is shown now. Before, I would get 
Not software rendered: yes and Unity supported: Yes
but suddenly my graphics card doesnt support unity anymore...
What happened?????

(btw I installed the xorg drivers after the bug happened. Before i installed the xorg drivers this problem occured) Thank you.

---

### Post by Basher101 on 2011-12-08
sounds like a video driver issue or bug...since i have absoluteley no experience regarding this, you will have to wait until someone answers that has the knowledge...im out


regards

---

### Post by BC59 on 2011-12-08
Try first the easy solutions. 
Reset Unity:

```
unity --reset
```

If this doesn't work then reinstall Unity

```
sudo apt-get install --reinstall unity
```

---

