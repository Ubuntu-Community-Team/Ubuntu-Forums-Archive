---
title: "&quot;No such file or directory&quot; when executing an existing file"
date: 2011-02-01
forum: General Help
---

### Post by KeiNivky on 2011-02-01
Same problem of this topic: [http://www.uluga.ubuntuforums.org/showthread.php?t=1054621](http://www.uluga.ubuntuforums.org/showthread.php?t=1054621)

I am trying to run 32-bit executable in 64-bit system and it says "no such file or directory". I tried installing the libs they mentioned in the topic but they were already on my system.

It may be relevant to say that this happens only when I use the C standard lib, specifically the printf function. Later I'll write programs using other functions to see what happens. 

And, yes. The file really is an exec and the permission are set right.

**edit:**
I tried to link using ld (GNU linker) instead of gcc, and now the executable works. :confused:
Someone has any idea why this is happening?

---

