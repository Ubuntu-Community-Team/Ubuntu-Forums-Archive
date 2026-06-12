---
title: "Package Install Loop"
date: 2006-05-23
forum: General Help
---

### Post by scabootssca on 2006-05-23
I'm trying to install packages and one of the packages i'm trying to install needs g++ so i try to install it and it needs libstdc++ but that needs g++ but that needs  libstdc++ and i'm stuck in a never-ending loop and cant think of a solution.](*,)

---

### Post by nanotube on 2006-05-23
try installing "build-essential" package, that should pull all that stuff in automagically.

---

### Post by salem7 on 2006-05-23
Tried that... worked for me!

---

### Post by mcduck on 2006-05-23
by the way, next time you have this kind of problem just install all packages at the same time, like 'sudo apt-get install package1 package2'.

---

