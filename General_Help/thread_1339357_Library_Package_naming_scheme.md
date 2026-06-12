---
title: "Library Package naming scheme"
date: 2009-11-27
forum: General Help
---

### Post by kulkarniniraj on 2009-11-27
Hi
  I have a question that how ubuntu library packages are named?
I mean in synaptic i can see lot of packages beginning with lib prefix
like libc etc, and there are some packages which contain a postfix '-dev'.
  It's understandable that it contains development headers, but it also contains some .a and .so files. Now the confusion is generally only 'lib' packages also contain shared libraries with extension .so.2.0.01 etc.
eg: libmad0 package contains /usr/lib/libmad.so.0.2.1 
and libmad0-dev contains /usr/lib/libmad.so  & /usr/lib/libmad.a
so why reinstall .so.0.2.1 package with .so and why both .a as well as .so for same package are needed.
   Also while linking which library is linked by default (.a or .so) or is it like windows dll where u link .lib first and .dll dynamically?
    Also why only few libraries contain doc pacage like lib*-doc? what abt documentation of other libraries?
Thank you

---

