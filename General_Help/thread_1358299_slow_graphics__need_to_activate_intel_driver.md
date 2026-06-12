---
title: "slow graphics / need to activate intel driver?"
date: 2009-12-18
forum: General Help
---

### Post by gorgon on 2009-12-18
Hi all!

Im running karmic xubuntu on a machine where ubuntu with gnome has been running quite smoothly before. Now with xfce it seems slower - firefox was so slow that I changed to swiftfox, and thats slightly better, but still the graphics are considerably slower than with gnome. This should really be the other way around, thus my suspicion that Im not correctly calibrated.

after reading the X troubleshooting page on the wiki I had a look in glxinfo:
```

(~) % glxinfo | grep OpenGL 
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.6
OpenGL shading language version string: 1.20
OpenGL extensions:

```

But it doesnt make me MUCH smarter :( Although I have a suspicion that rendering things with software makes stuff go slower... My graphics is:
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller.

Anyone know what to do or where to look?

Thanks,
g

---

### Post by gorgon on 2009-12-18
further research show that in Ubuntu/Gnome, that I got installed on the same machine, there are different drivers in use:

```

gorgon@ubuntu:~$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
OpenGL version string: 1.4 (2.0 Mesa 7.4)
OpenGL extensions:

```

Now, how can I switch the driver to Intel (or Tungsten, Mesa DRI Intel) like the setup I got in Gnome in xfce?

---

### Post by gorgon on 2009-12-18
ok, I found the solution [here]("http://www.klabs.be/~fpiat/linux/debian/Lenny_on_Thinkpad_T61.html#Display"), I had to install the mesa opengl drivers:
```
sudo apt-get install mesa-utils libgl1-mesa-dri xlibmesa-gl xlibmesa-glu
```

and now all is good, apparently :)

---

### Post by klemes on 2009-12-18
Maybe you should try to use the Xorg.conf file from your other installation.
Or alternatively you could edit your present Xorg.conf and add 'Driver    "intel" '
in your Device section.

---

