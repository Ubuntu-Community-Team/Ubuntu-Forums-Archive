---
title: "SDL.H is missing NEED SERIOUS HELP!"
date: 2009-11-11
forum: General Help
---

### Post by frs89 on 2009-11-11
Hi

I installed SDL library through

```
sudo apt-get install libsdl1.2-dev

```And I included SDL.H in my prog like this
```
...
#include "SDL.h"
...

``````
gcc cursor.c -o cursor
cursor.c:7:17: error: SDL.h: No such file or directory

```and I checked that in usr/lib/include/SDL/SDL.h exists! 

What I need to do to compile my program?

Thanks

---

