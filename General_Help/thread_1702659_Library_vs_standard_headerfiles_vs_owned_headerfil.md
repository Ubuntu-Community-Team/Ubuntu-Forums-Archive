---
title: "Library vs standard headerfiles vs owned headerfiles"
date: 2011-03-08
forum: General Help
---

### Post by sravfeyn on 2011-03-08
I am trying to use ncurses headerfile in a program. i am on ubuntu 10 and the ncurses package 5.7 is already installed on it. I have included in my C program "include <ncurses.h>"
i have compiled program by the command "gcc -std=c99 -o progname progname.c -lncurses"
but still gcc says "ncurses.h: no such file or directory"
and i have searched for ncurses.h but i couldn't find it on the system.
the problem is more fundamental. howz library different from headerfiles. and why all headerfiles are available by default.?? and also how can i add my own headerfiles to the the standard list than on current working directory??
someone help plz!!

---

### Post by Vaphell on 2011-03-08
if you want to compile stuff you need *-dev flavor of packages to get headers.
Most likely libncurses5-dev is the one you want.

Header files are not available by default, only those that were installed. When you install C and C++ you get a complete set of headers that belong to the standard library. Any additional library needs its own set of headers to be usable in your own code.
Headers describe the interface of the library (available functions, types, classes, returned types) and are required by compiler, without them it wouldn't know what to expect and would not be able to check for errors like type mismatch or undefined class/function. Compiled program uses compiled versions of libraries stored in some standard location in the system ('normal' versions of libraries) but for compilation purposes you need a 'raw' devel version with all the inner workings exposed.
It's like the difference between menu and a cookbook. Menu lists ready meals which is fine when you are a customer but to make them you need detailed recipes.

and why would you want to move your program specific headers away from your working directory?

---

