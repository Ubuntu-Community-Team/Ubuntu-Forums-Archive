---
title: "login problem 3d for 11.10"
date: 2011-10-20
forum: General Help
---

### Post by SwintonStreet on 2011-10-20
Hi I've recently updated to 11.10 and now its not allowing me to login in regular (3d) mode.

I can still login in 2d with no problems and a bit puzzled...

Any ideas?

---

### Post by gandaran on 2011-10-20
> **SwintonStreet said:**
> Hi I've recently updated to 11.10 and now its not allowing me to login in regular (3d) mode.

I can still login in 2d with no problems and a bit puzzled...

Any ideas?
did you install drivers?
run this test
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by SwintonStreet on 2011-10-20
Thanks for the quick reply, I got,


```
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string:  2.1 Mesa 7.12-devel

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

### Post by gandaran on 2011-10-21
well, the video card supports 3D so it's probably something to do with the user account settings, did you do a clean install or upgraded?
try creating another account to see if 3D unity works on it.

---

### Post by SwintonStreet on 2011-10-21
I have tried creating a new account, same issue. It'll load the background and mouse, but no more.

I upgraded to 11.10 from 11.04.

Thanks for the help.

---

### Post by dsk1 on 2011-10-22
i've got the same problem, does ayone know how to fix it? :(

---

### Post by masgeeks on 2011-10-22
Try a clean install...

---

### Post by dsk1 on 2011-10-22
I installed it 3 times and this problem occurs everytime. 2D works fine but i want a 3D. Any ideas?

---

### Post by SwintonStreet on 2011-10-23
I have somewhat solved the issue.

I installed edgers-ppa,

[http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)

This solved my problems of glx gears not working. However I was still unable to use 3D.

To solve this I purged edgers (using ppa-purge), reinstalled xorg and rebooted. It would only load in terminal mode.

A friend then used the code

```

sudo apt-get install xorg

```

However it appears that the problem is a bug for edgers using nvidia, this may be sored very soon?

[http://www.ubuntuupdates.org/ppas/87](http://www.ubuntuupdates.org/ppas/87)

This has updates for edgers, I may go back in the future, just happy to have a 3D gui with glx.

---

