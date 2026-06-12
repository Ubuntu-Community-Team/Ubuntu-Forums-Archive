---
title: "Pygame 1.9.1 for python 3.2 Ubuntu Help"
date: 2012-03-19
forum: General Help
---

### Post by touches on 2012-03-19
Hello Ubuntu Forum

I have installed pygame 1.9.1 for python 3.2 using the following commands
[B]"python3 config.py
python3 setup.py build
phython3 setup.py install [/B]"

The installation was successful and when i tried to import pygame from python 3.2 i get the following error

[B]>>> import pygame
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python3.2/site-packages/pygame/__init__.py", line 95, in <module>
    from pygame.base import *
ImportError: /usr/local/lib/python3.2/site-packages/pygame/base.cpython-32m.so: undefined symbol: PyCObject_Check[/B]

I am very much new to Ubuntu and this is my first time installation of Python and Pygame. Please help me out on sorting this out. I read that for python 3.2 one must install pygame 1.9.2?? If so then how to remove the older version of pygame??

PS: how to get the code tags to work??

---

### Post by touches on 2012-03-20
Any help please. I really want to start learning Pygame and Python

---

### Post by PatrickReilly on 2012-04-14
Go to here
[http://www.pygame.org/wiki/CompileUbuntu?parent=Compilation]("http://www.pygame.org/wiki/CompileUbuntu?parent=Compilation")

---

