---
title: "Display arrows in terminal?"
date: 2010-04-14
forum: General Help
---

### Post by hammadr89 on 2010-04-14
Hi, I'm running the 9.10 netbook remix... well, the thing is, me and a few of my friends designed this game which involved displaying arrows (in C). Now we designed it using Dev-C++ and under the windows command prompt, they showed up fine. But I tried running it in the terminal, and the arrows wouldn't show up right. They'd just be boxes with numbers or letters in them. The ASCII values for the arrows are 24 - 27 from what I know. Is there anything I can do to fix this?

I made one modification to the code. It used the library windows.h, and I searched on google, so I did this:

#ifndef linux
#include <windows.h>
#endif

and that seemed to do the trick, apart from the arrows issue. Thanks

---

