---
title: "Fluxbox 1.0.0 Error"
date: 2010-01-10
forum: General Help
---

### Post by jhfire on 2010-01-10
I'm a total nub to Ubuntu and really need some help with this. I can't find anything helpful online, so here I am asking the Ubuntu community :D. The error I'm getting is below.

[CENTER]```
main.cc: In function ‘void showInfo(std::ostream&)’:
main.cc:71: error: ‘strlen’ was not declared in this scope
make[4]: *** [main.o] Error 1
make[4]: Leaving directory `/home/james/Desktop/fluxbox-1.0.0/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/james/Desktop/fluxbox-1.0.0/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/james/Desktop/fluxbox-1.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/james/Desktop/fluxbox-1.0.0'
make: *** [all] Error 2

```[/CENTER]

I'm getting that error when I enter in "make".

---

### Post by jhfire on 2010-01-10
bump

---

### Post by Barriehie on 2010-01-21
A function is being called that's not defined in the code block where it's being called.  Did you do any editing of your source code and did you get it from the repos???

---

