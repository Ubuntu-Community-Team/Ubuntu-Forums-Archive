---
title: "graphics problem"
date: 2011-01-16
forum: General Help
---

### Post by neonic on 2011-01-16
Hello, I'm using ubuntu 10.04 with an ati radeon x1600 Pro card and I have problems with my graphics I believe. This is what I get when I try to run teeworlds:

```

[4d32ebc2][gfx]: unable to set video mode: Couldn't find matching GLX visual
[4d32ebc2][gfx]: out of ideas. failed to init graphics

```

and when I do glxinfo I get:

```

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

```

Does anyone know where I should look to find the problem?

---

