---
title: "xserver error: could not open default font 'fixed'"
date: 2006-03-25
forum: General Help
---

### Post by tioneb on 2006-03-25
Hi,

I installed dapper in server mode then these three packages
xserver-xorg wmaker wdm

when wdm is launched, I get a black screen after 10 sec I go back to the terminal
when I launch wmaker I get a fatal error
WindowMaker can not find the display ""

the fatal error in xorg.0.log is
```
could not open default font 'fixed'
```

I've tried dpkg-reconfigure with all packages without success
I need help on that
thanks

---

### Post by tioneb on 2006-05-05
package "xfonts-base"

---

