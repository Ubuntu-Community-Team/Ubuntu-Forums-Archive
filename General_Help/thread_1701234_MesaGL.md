---
title: "MesaGL"
date: 2011-03-06
forum: General Help
---

### Post by snl on 2011-03-06
If I need OpenGL and Glut libraries, which of the Mesa package do I need to install?

```

p   libegl1-mesa                    - A free implementation of the EGL API -- ru
p   libegl1-mesa-dbg                - A free implementation of the EGL API -- de
p   libegl1-mesa-dev                - A free implementation of the EGL API -- de
p   libegl1-mesa-drivers            - A free implementation of the EGL API -- ha
p   libegl1-mesa-drivers-dbg        - A free implementation of the EGL API -- dr
p   libgl1-mesa-dev                 - A free implementation of the OpenGL API --
i   libgl1-mesa-dri                 - A free implementation of the OpenGL API --
p   libgl1-mesa-dri-dbg             - Debugging symbols for the Mesa DRI modules
v   libgl1-mesa-dri-dev             -                                           
p   libgl1-mesa-dri-experimental    - A free implementation of the OpenGL API --
p   libgl1-mesa-dri-experimental-db - Debugging symbols for the experimental Mes
i   libgl1-mesa-glx                 - A free implementation of the OpenGL API --
p   libgl1-mesa-glx-dbg             - Debugging symbols for the Mesa GLX runtime
v   libgl1-mesa-swrast              -                                           
v   libgl1-mesa-swrast-dbg          -                                           
v   libgl1-mesa-swrast-dev          -                                           
p   libgl1-mesa-swx11               - A free implementation of the OpenGL API --
p   libgl1-mesa-swx11-dbg           - A free implementation of the OpenGL API --
p   libgl1-mesa-swx11-dev           - A free implementation of the OpenGL API --
p   libgles1-mesa                   - A free implementation of the OpenGL|ES 1.x
p   libgles1-mesa-dbg               - A free implementation of the OpenGL|ES 1.x
p   libgles1-mesa-dev               - A free implementation of the OpenGL|ES 1.x
p   libgles2-mesa                   - A free implementation of the OpenGL|ES 2.x
p   libgles2-mesa-dbg               - A free implementation of the OpenGL|ES 2.x
p   libgles2-mesa-dev               - A free implementation of the OpenGL|ES 2.x
i   libglu1-mesa                    - The OpenGL utility library (GLU)          
p   libglu1-mesa-dev                - The OpenGL utility library -- development 
p   libglw1-mesa                    - A free implementation of the OpenGL API --
p   libglw1-mesa-dev                - A free implementation of the OpenGL API --
p   libopenvg1-mesa                 - A free implementation of the OpenVG API --
p   libopenvg1-mesa-dbg             - A free implementation of the OpenVG API --
p   libopenvg1-mesa-dev             - A free implementation of the OpenVG API --
v   libosmesa-dev                   -                                           
p   libosmesa6                      - Mesa Off-screen rendering extension       
p   libosmesa6-dev                  - Mesa Off-screen rendering extension -- dev
p   mesa-common-dev                 - Developer documentation for Mesa          
p   mesa-utils                      - Miscellaneous Mesa GL utilities           
v   mesag-dev                       -                                           
v   mesag-widgets-dev               -                                           
v   mesag3                          -                                           
v   mesag3-widgets                  -                                           
p   xlibmesa-gl                     - transitional package for Debian etch      
p   xlibmesa-gl-dev                 - transitional package for Debian etch      
p   xlibmesa-glu                    - transitional package for Debian etch      
v   xlibmesa-glu-dev                -                                           
v   xlibosmesa-dev                  -            

```

Thank you in advance

---

### Post by Yellow Pasque on 2011-03-06
If you need libraries to link against, then libgl1-mesa-dev and libglu1-mesa-dev should do the trick.

---

### Post by snl on 2011-03-07
Thank you for your reply. I have installed both libgl1-mesa-dev and libglu1-mesa-dev but still got the following error message

```
fatal error: GL/glut.h: No such file or directory
```

Please advise.
Thanks.

---

### Post by snl on 2011-03-07
> **snl said:**
> Thank you for your reply. I have installed both libgl1-mesa-dev and libglu1-mesa-dev but still got the following error message

```
fatal error: GL/glut.h: No such file or directory
```

Please advise.
Thanks.

```
sudo aptitude install freeglut3-dev
```
did the trick :)

Thanks.

---

### Post by HermanAB on 2011-03-07
Howdy,

Typically, if you play with OpenGL applications, you need pretty much all of those packages, since somewhere down the line, something will need it and usually these programs are not very nice about telling what they need, they just fall over.  So you can just as well search for glut, glew, glx and mesa and install everything and anything that comes up that looks remotely useful...

---

