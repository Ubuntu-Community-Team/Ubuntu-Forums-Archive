---
title: "PyOpenGL fails to load correctly when locale is not English"
date: 2009-12-04
forum: General Help
---

### Post by Tiede on 2009-12-04
Hey all,
We are developing a program using python and OpenGL and ran into this:
If the computer's language is set to english, the program will compile and run correclty. However, switching the language to french before logging in makes it crash! The traceback says it's looking for GL and failing to find it... Anyone knows how I can fix this issue?

My Specs:
```

tiede@laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
tiede@laptop:~$ uname -a
Linux laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux

```

The output of the import in french:
```

>>>from OpenGL import GL
Traceback (most recent call last):
  File "<input>", line 1, in <module>
  File "/usr/local/lib/python2.6/dist-packages/PyOpenGL-3.0.1b1-py2.6.egg/OpenGL/GL/__init__.py", line 2, in <module>
    from OpenGL.raw.GL import *
  File "/usr/local/lib/python2.6/dist-packages/PyOpenGL-3.0.1b1-py2.6.egg/OpenGL/raw/GL/__init__.py", line 6, in <module>
    from OpenGL.raw.GL.constants import *
  File "/usr/local/lib/python2.6/dist-packages/PyOpenGL-3.0.1b1-py2.6.egg/OpenGL/raw/GL/constants.py", line 7, in <module>
    from OpenGL import platform, arrays
  File "/usr/local/lib/python2.6/dist-packages/PyOpenGL-3.0.1b1-py2.6.egg/OpenGL/platform/__init__.py", line 36, in <module>
    _load()
  File "/usr/local/lib/python2.6/dist-packages/PyOpenGL-3.0.1b1-py2.6.egg/OpenGL/platform/__init__.py", line 27, in _load
    plugin_class = plugin.load()
  File "/usr/local/lib/python2.6/dist-packages/PyOpenGL-3.0.1b1-py2.6.egg/OpenGL/plugins.py", line 14, in load
    return importByName( self.import_path )
  File "/usr/local/lib/python2.6/dist-packages/PyOpenGL-3.0.1b1-py2.6.egg/OpenGL/plugins.py", line 28, in importByName
    module = __import__( ".".join(moduleName), {}, {}, moduleName)
  File "/usr/local/lib/python2.6/dist-packages/PyOpenGL-3.0.1b1-py2.6.egg/OpenGL/platform/glx.py", line 8, in <module>
    class GLXPlatform( baseplatform.BasePlatform ):
  File "/usr/local/lib/python2.6/dist-packages/PyOpenGL-3.0.1b1-py2.6.egg/OpenGL/platform/glx.py", line 16, in GLXPlatform
    mode=ctypes.RTLD_GLOBAL
  File "/usr/local/lib/python2.6/dist-packages/PyOpenGL-3.0.1b1-py2.6.egg/OpenGL/platform/ctypesloader.py", line 53, in loadLibrary
    return dllType( name, mode )
  File "/usr/lib/python2.6/ctypes/__init__.py", line 353, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: ("GL: Ne peut ouvrir le fichier d'objet partag\xc3\xa9: Aucun fichier ou dossier de ce type", 'GL', None)

```

Oh! I have also filed a [launchpad bug report](https://bugs.launchpad.net/ubuntu/+source/pyopengl/+bug/490463) about this... (bug#[490463](https://bugs.launchpad.net/ubuntu/+source/pyopengl/+bug/490463)).

If you've seen this before or know why it's happening, do let me know, including how I can fix it, hopefully!

---

### Post by Tiede on 2009-12-07
no one ever heard of this before?

---

