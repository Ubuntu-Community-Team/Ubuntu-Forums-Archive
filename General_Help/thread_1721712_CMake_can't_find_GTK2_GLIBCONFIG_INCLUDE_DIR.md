---
title: "CMake can't find GTK2_GLIBCONFIG_INCLUDE_DIR"
date: 2011-04-04
forum: General Help
---

### Post by cheapie on 2011-04-04
I've tried installing all packages that look like they have anything to do with GTK, but CMake still says "Some or all of the gtk libraries were not found. (missing:  GTK2_GLIBCONFIG_INCLUDE_DIR)" and the build fails. What do I need to do to fix this?

P.S.: I'm running Natty. I couldn't find a board for problems with Natty, which is why I posted this here. If such a board exists, and you're a moderator/admin, please move it.

---

### Post by gusnan on 2011-04-10
See
[https://bugs.launchpad.net/ubuntu/+source/cmake/+bug/751940](https://bugs.launchpad.net/ubuntu/+source/cmake/+bug/751940)

Its a known bug in Natty version of CMake.

---

