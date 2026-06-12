---
title: "coming back to nvidia driver from package"
date: 2009-09-21
forum: General Help
---

### Post by clement.analogue on 2009-09-21
Hello,

I installed the driver from the nvidia website (to enable agp fw and sba) but I could not enable compiz-fusion.
I change my GC (pci) and I want to using again the driver from the packages (hoping enable the compiz-fusion effects). So I uninstalled the drivers, next I installed the modaliases (nvidia-glx-180) but there isn't any driver in the "hardware drivers".

To fixe it, I installed the package nvidia-glx-180 but I still can't enable the graphical effects. When I try to enable this effect in "visual effects", I've got a windows "searching for available drviers", next I've got the message "Desktop effects could not be enabled"

In a terminal,
```
glxinfo | grep direct 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
etc.
```
same thing with
```
glxinfo | grep "OpenGL version"
```

thanks for helping.

---

