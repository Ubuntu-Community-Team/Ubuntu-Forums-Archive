---
title: "help installing libtcod"
date: 2009-12-02
forum: General Help
---

### Post by karimruan on 2009-12-02
I am trying to install libtcod-1.4.1 into /usr/local/lib/python2.6/dist-packages, but it says "Permission Denied". If I do it from the terminal, using 
```

sudo cp libtcod-1.4.1 /usr/local/lib/python2.6/dist-packages

```

it tells me:

libtcod-1.4.1 was omitted. 

I really want to learn to write a roguelike in python, it is my language of choice, and I have many good ideas. I had this problem install easygui, but using sudo cp worked for it. Any ideas?

I also wrote a bash script to sudo cp all the files into /dist-packages, but when i try to run the code i am working on, it gives me the following output:

```

File "pyrogue1.py", line 8, in <module>
    import libtcodpy as libtcod
  File "/usr/local/lib/python2.6/dist-packages/libtcodpy.py", line 33, in <module>
    _lib = ctypes.cdll['./libtcod.so']
  File "/usr/lib/python2.6/ctypes/__init__.py", line 428, in __getitem__
    return getattr(self, name)
  File "/usr/lib/python2.6/ctypes/__init__.py", line 423, in __getattr__
    dll = self._dlltype(name)
  File "/usr/lib/python2.6/ctypes/__init__.py", line 353, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: ./libtcod.so: cannot open shared object file: No such file or directory
mat@mat-laptop:~$ 

```

this is the contents of /dist-packages:

```

circle.png  easygui.py  libSDL.so  libtcod-gui.so  libtcodpy.py  libtcod.so  libtcod++.so  samples_c.c  samples_cpp.cpp  samples_py.py  terminal.png

```

---

### Post by karimruan on 2009-12-02
even if you could point me to a more, well documented method of making a roguelike in python, or even another similar (simple) language. I am not ready for C++ or java yet. (Maybe java).

What it the easiest language used commonly for roguelikes? I prefer to have an IDE that indents for me. Interpreters are great, i hate compiling, never got it right,

EDIT:

I know, I know, easiest is very subjective. I am looking for opinions, though, so....

---

