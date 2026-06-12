---
title: "cannot find -lGLU Error during make"
date: 2010-03-28
forum: General Help
---

### Post by Goblin82 on 2010-03-28
Hi, I'm trying to compile gtkglArea-1.99.0 but I think I'm running into a linking error.  This is the error exactly : /usr/bin/ld: cannot find -lGLU.  I have the OpenGL and GTK+ libraries, well ./configure runs with no errors so I assume I have everything I need.  Does anyone know how to fix the error in order for me to run make properly? Thanks. :)

---

### Post by stilling on 2010-03-28
have you tried first to go to System -> Administration -> synaptic package manager and write in the search box gtkglarea and simply click on the square in the front of the name and apply and that is it no errors



hope this helps

---

### Post by Goblin82 on 2010-03-28
Thanks bud! that installed the package and the others I needed but now I need to add a path to PKG_CONFIG_PATH because I need to point to tao-opengl.pc file.  how do I modify the pkg-config file to add the correct path?

---

