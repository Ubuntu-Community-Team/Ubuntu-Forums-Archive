---
title: "compile PyCairo against newly build Cairo libs"
date: 2010-04-24
forum: General Help
---

### Post by mayapower on 2010-04-24
Hi,

I have just compiled cairo on ubuntu hardy (cairo 1.8.10, pixman  0.18.0). All the libraries are in /usr/local/. When I am compiling  pycairo 1.8.8 using "python setup.py install", I am getting an error:
```

Package 'cairo' requires 'pixman-1 >= 0.12.0' but version of Pixman is 0.10.0
Error: cairo >= 1.8.8 not found

```
it seems it's still have no clue about newly installed libs. How do I set path/vars to build pycairo against the  newly installed libs?

I tried setting up these vars before installing:
```

export LD_LIBRARY_PATH=/usr/local/lib
export CAIRO_LIBS=/usr/local/lib
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig

```

but still no luck.

Cheers

Prashant

---

### Post by pragya on 2010-12-31
hey, I am facing a similar sort of problem


Perhaps you should add the directory containing `cairo.pc'
to the PKG_CONFIG_PATH environment variable
No package 'cairo' found

Were you able to solve your problem??

Thanks,
Pragya

---

### Post by pragya on 2010-12-31
hey, I am facing a similar sort of problem


Perhaps you should add the directory containing `cairo.pc'
to the PKG_CONFIG_PATH environment variable
No package 'cairo' found

Were you able to solve your problem??

Thanks,
Pragya

---

