---
title: "GCC exit status 1"
date: 2009-12-13
forum: General Help
---

### Post by Alan502 on 2009-12-13
Hi :) im trying to install pygame 1.9 in my kubuntu amd64 but when i run the setup.py the compiler exits with: error: command 'gcc' failed with exit status 1

alan@alan-desktop:~/Downloads/fofix-3.121/src/pygame-1.9.1release$ python setup.py build                                                                                                                                                                 
running build                                                                                                                                                                                                                                            
running build_py                                                                                                                                                                                                                                         
running build_ext                                                                                                                                                                                                                                        
building 'pygame._numericsurfarray' extension                                                                                                                                                                                                            
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -D_REENTRANT -I/usr/X11R6/include -I/usr/include/SDL -I/usr/include/python2.6 -c src/_numericsurfarray.c -o build/temp.linux-x86_64-2.6/src/_numericsurfarray.o
In file included from src/_numericsurfarray.c:23:
src/pygame.h:75:20: error: Python.h: No such file or directory
In file included from src/_numericsurfarray.c:23:
src/pygame.h:122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lenfunc’
src/pygame.h:123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizeargfunc’
src/pygame.h:124: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizeobjargproc’
src/pygame.h:125: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizessizeargfunc’
src/pygame.h:126: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizessizeobjargproc’
src/pygame.h:127: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘readbufferproc’
src/pygame.h:128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘writebufferproc’
src/pygame.h:129: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘segcountproc’
src/pygame.h:130: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘charbufferproc’
src/pygame.h:234: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:275: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:310: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:349: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:387: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:450: error: expected specifier-qualifier-list before ‘PyObject’
src/pygame.h:457: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:499: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:567: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
In file included from src/_numericsurfarray.c:25:
src/numeric_arrayobject.h:66: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/numeric_arrayobject.h:67: error: expected ‘)’ before ‘*’ token
src/numeric_arrayobject.h:72: error: expected specifier-qualifier-list before ‘PyArray_GetItemFunc’
src/numeric_arrayobject.h:92: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/numeric_arrayobject.h:114: error: expected specifier-qualifier-list before ‘Py_intptr_t’
src/_numericsurfarray.c:28: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:100: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:140: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:189: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:290: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:431: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:536: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:651: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:835: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:1058: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/_numericsurfarray.c:1121: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘surfarray_builtins’
src/_numericsurfarray.c: In function ‘init_numericsurfarray’:
src/_numericsurfarray.c:1148: error: ‘PyObject’ undeclared (first use in this function)
src/_numericsurfarray.c:1148: error: (Each undeclared identifier is reported only once
src/_numericsurfarray.c:1148: error: for each function it appears in.)
src/_numericsurfarray.c:1148: error: ‘_module’ undeclared (first use in this function)
src/_numericsurfarray.c:1148: warning: implicit declaration of function ‘PyImport_ImportModule’
src/_numericsurfarray.c:1148: error: ‘_dict’ undeclared (first use in this function)
src/_numericsurfarray.c:1148: warning: implicit declaration of function ‘PyModule_GetDict’
src/_numericsurfarray.c:1148: error: ‘_c_api’ undeclared (first use in this function)
src/_numericsurfarray.c:1148: warning: implicit declaration of function ‘PyDict_GetItemString’
src/_numericsurfarray.c:1148: warning: implicit declaration of function ‘PyCObject_Check’
src/_numericsurfarray.c:1148: warning: implicit declaration of function ‘PyCObject_AsVoidPtr’
src/_numericsurfarray.c:1148: warning: cast to pointer from integer of different size
src/_numericsurfarray.c:1148: warning: implicit declaration of function ‘Py_DECREF’
src/_numericsurfarray.c:1149: warning: implicit declaration of function ‘PyErr_Occurred’
src/_numericsurfarray.c:1152: warning: cast to pointer from integer of different size
src/_numericsurfarray.c:1152: warning: cast to pointer from integer of different size
src/_numericsurfarray.c:1156: error: ‘numpy’ undeclared (first use in this function)
src/_numericsurfarray.c:1156: error: ‘module_dict’ undeclared (first use in this function)
src/_numericsurfarray.c:1156: error: ‘c_api_object’ undeclared (first use in this function)
src/_numericsurfarray.c:1156: warning: cast to pointer from integer of different size
src/_numericsurfarray.c:1162: warning: implicit declaration of function ‘Py_InitModule3’
src/_numericsurfarray.c:1162: error: ‘surfarray_builtins’ undeclared (first use in this function)
**error: command 'gcc' failed with exit status 1**
alan@alan-desktop:~/Downloads/fofix-3.121/src/pygame-1.9.1release$


What could be the problem here?

---

### Post by Some Penguin on 2009-12-13
The first problem is --

src/pygame.h:75:20: error: Python.h: No such file or directory

See [http://ubuntuforums.org/showthread.php?t=497109](http://ubuntuforums.org/showthread.php?t=497109)

---

