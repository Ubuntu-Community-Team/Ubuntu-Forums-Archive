---
title: "Not sure if Mesa 7.11 installed correctly"
date: 2011-09-06
forum: General Help
---

### Post by Helios747 on 2011-09-06
Hello,

I'm running Ubuntu 10.04 64 bit on my ASUS K53E. After following a few tutorials I got the sandybridge GPU working correctly after installing a few PPAs upgrading packages, and installing a Natty backported kernel.


I read that Mesa 7.11 has increased performance for Sandybridge GPUs. I wanted to get in on that.


I downloaded the mesalib and MesaGLUT tarballs, got those compiled properly after a bit of tinkering. Make install SAYS it completed without error. I reboot, and run ""glxinfo | grep OpenGL" to verify that I'm running 7.11

```
anthony@anthony-laptop:~$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile GEM 20100330 DEVELOPMENT 
OpenGL version string: 2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20
OpenGL extensions:

```Still says it's on 7.10.2. Is it lying to me? make && sudo make install completed without error.

Did the mesa drivers not update the version string? Did I forget to upgrade something? I upgraded mesalib and MesaGLUT straight from the mesa3d homepage, following their instructions.

The dependencies and whatnot I used to compile with came from the ubuntu repos.

EDIT: It was suggested elsewhere in a thread I read to install the xorg-edgers PPA, for me that just broke X the first time I tried this. I'd prefer not to try that again. Haha.

---

### Post by Helios747 on 2011-09-07
bumpity.

---

### Post by Helios747 on 2011-09-07
Fixed it. For some reason the install script was placing the compiled library files in /usr/local/lib, instead of /usr/lib.

Moving the files manually worked.

The commands I used (AFTER RUNNING THE FLAWED INSTALL SCRIPT, make sure you do that first, as I don't know where the DRI files are in this folder, but I know where they're installed to.)

```
anthony@anthony-laptop:~/Downloads/Mesa-7.11$ sudo cp lib/* /usr/lib/

anthony@anthony-laptop:~/Downloads/Mesa-7.11$ sudo cp /usr/local/lib/dri/* /usr/lib/dri*

```

Reboot, after rebooting, you should be running mesa 7.11

```
anthony@anthony-laptop:~/Downloads/Mesa-7.11$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:

```


Hope this helps!

---

