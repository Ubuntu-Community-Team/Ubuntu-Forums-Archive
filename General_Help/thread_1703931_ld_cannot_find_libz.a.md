---
title: "ld cannot find libz.a"
date: 2011-03-09
forum: General Help
---

### Post by RobotGymnast on 2011-03-09
I'm trying to compile a simple SFML test project, but whenever I try, I get an error message from ld, telling me it can't find the library I want. To simplify things, I just made the most basic test cpp file ever, and tried linking it with /usr/lib/libz.a. This is my output:

```
me@lappy486:~/devl/c++/SFMLTest$ gcc-4.5 main.cpp -llibz.a
/usr/bin/ld: cannot find -llibz.a
collect2: ld returned 1 exit status

```

Any ideas?

---

### Post by RobotGymnast on 2011-03-10
Solved - turns out the -l flag automatically adds in the lib prefix and the .a suffix.

---

