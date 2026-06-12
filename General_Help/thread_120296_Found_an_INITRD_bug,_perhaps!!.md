---
title: "Found an INITRD bug, perhaps?!?!"
date: 2006-01-21
forum: General Help
---

### Post by ashrack on 2006-01-21
Thus far have learned a great deal about kernel compiling and have also compiled lots of working kernels by now. Tanx to the great community here.

But the following thing is still bugging me:
I use REISERFS and under REISERFS option in MENUCONFIG I've set * from the default M(module)
But now when I boot the kernel I get an error message:
```
FATAL:Module REISERFS NOT FOUND
```
BUt the systems works perfectly well than.
This only happens if I compile the kernel thru '--initrd' switch.  It's my believe that there's a BUG in the INITRD script which automaticly assumes that the FS is compiled as a MODULE and it doesn't check first if it has been already compiled into the kernel. Is there a way to fix this? Since the FATAL error on every reboot is bugging me greatly.

---

### Post by ashrack on 2006-01-21
bump

---

