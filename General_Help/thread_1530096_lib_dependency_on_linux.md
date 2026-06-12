---
title: "lib dependency on linux"
date: 2010-07-13
forum: General Help
---

### Post by mayapower on 2010-07-13
Hi,

Using custom python package creator, I am creating a self-sufficient package that would hopefully run on systems where python is not installed.

I am using "hardy 8.04" and every thing(python, wxpython, cairo, pixman etc.) is compiled
on it.
LIBS USED
```

cairo 1.8.10
pixman 0.18.0
pycairo 1.8.8 (_cairo.so)
python 2.6.5 rc5
wxpython 2.8.10.1

```App is running fine on karmic but there is slight problem.When I am executing command
```

ldd _cairo.so

```on karmic, in the list of dependencies it's pointing to libraries(cairo, pixman) which are in /usr/lib directory. It seems it's not using the libs that I am including with the package.
App is running fine because libs installed on karmic(1.8.8) are compatible with _cairo.so, 
I tried these three settings so that _cairo.so use libs that comes with the package:

1. Copying cairo & pixman libs to the same directory where _cairo.so is
2. Copying cairo & pixman libs where my package's python lib is
3. setting up "LD_LIBRARY_PATH" and point to the directory where my cairo & pixman libs are before executing app.

It seems none of these settings are working. How do I make sure that _cairo.so use libs that I am including with and not the one present in the system.

In another test, I manually removed cairo and pixman libs from the /usr/lib/ directory and app is running fine (LD_LIBRARY_PATH setting). It means _cairo.so is using correct libs(installed with package). Confusion still exists and I don't know when libs are present in both places, which one are used by _cairo.so?

I AM NEW TO LINUX & GETTING MY HANDS ON IT.

Cheers

Prashant

---

