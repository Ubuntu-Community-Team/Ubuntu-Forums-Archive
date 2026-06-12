---
title: "Ld_library_path"
date: 2009-11-07
forum: General Help
---

### Post by Tobywuk on 2009-11-07
Im trying to write an 'interpositioner' for a project and log all calls made to the socket() shared library function by all programs on ubuntu. My interpositioner is my own shared C library with the function socket() in it which does a printf(). I want programs to see this one before the normal socket() function in libc.

When i run a program that calls socket() with LD_PRELOAD, my own vershion of the socket() function gets called instead of the normal one and it works.

I am trying to produce the same thing with LD_LIBRARY_PATH so that all program that use the socket() function use my own custome made one. I want to be able to do this with out having to specify which shared lib to use each time when running a program.  

I have set LD_LIBRARY_PATH to that of my own (like with LD_PRELOAD) but it does not work.

Has anyone got any suggestions on how i can get this to work or achive the same results?

Thanks.

---

