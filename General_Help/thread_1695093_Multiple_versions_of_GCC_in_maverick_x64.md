---
title: "Multiple versions of GCC in maverick x64"
date: 2011-02-25
forum: General Help
---

### Post by Beowolf64 on 2011-02-25
I have installed GCC 4.5.1 using senaptic. But typing gcc in any terminal still calls the older version of gcc. I see that in /usr/bin gcc is a link to the older gcc. Would it be OK to replace that link with the new one poiting to the newer version of GCC?

Any input is appreciated. Thank you.

---

### Post by dino99 on 2011-02-25
yes if you glance at breakage, no for all the other cases :)

---

### Post by Beowolf64 on 2011-02-25
How about other tools? g++, gfortran, binary libs?

---

### Post by Beowolf64 on 2011-03-05
SOLVED (partially). Make links (gcc, g++, c++, cc, cpp, gcov, gfortran) in a private folder and prepend it to the PATH before using GCC. Don't make system wide changes.

---

