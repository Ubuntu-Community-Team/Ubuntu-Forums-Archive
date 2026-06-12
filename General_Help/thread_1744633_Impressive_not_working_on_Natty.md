---
title: "Impressive not working on Natty"
date: 2011-04-30
forum: General Help
---

### Post by pototo on 2011-04-30
Hello,

when I try tu run impressive I get the following output:

```
Welcome to Impressive version 0.10.3-WIP
Oops! Cannot load necessary modules: ('Unable to load OpenGL library', 'GL: cannot open shared object file: No such file or directory', 'GL', None)
To use Impressive, you need to install the following Python modules:
 - PyOpenGL [python-opengl]   http://pyopengl.sourceforge.net/
 - PyGame   [python-pygame]   http://www.pygame.org/
 - PIL      [python-imaging]  http://www.pythonware.com/products/pil/
 - PyWin32  (OPTIONAL, Win32) http://starship.python.net/crew/mhammond/win32/
Additionally, please be sure to have pdftoppm or GhostScript installed if you
intend to use PDF input.
```

Unity is working fine and modules python-opengl, python-pygame and python-imaging are installed. Running a freshly intalled and fully updated Natty.

Any ideas on what could be wrong?

---

### Post by pototo on 2011-05-06
OK, solved by installing package libgl1-mesa-dev.

More info in [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=509125](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=509125)

---

