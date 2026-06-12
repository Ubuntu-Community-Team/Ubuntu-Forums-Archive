---
title: "command mv works when moving to /usr/share but not cp?"
date: 2010-10-02
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-02
I just ran this command:


john@cmp:~/Downloads$ sudo cp * /usr/share/amsn/skins

and it came up with something like "cp omitting directory
 xxxx" for all directories (so each line xxxx was just a folder name.

I was trying to move all directories in my Downloads folder to the skins folder u see above.

But when I replaced the "cp" with "mv", it all worked fine. How come? I dont see why i can move but not copy?

---

### Post by dcstar on 2010-10-02
> **fuzzylogic25 said:**
> I just ran this command:


john@cmp:~/Downloads$ sudo cp * /usr/share/amsn/skins

and it came up with something like "cp omitting directory
 xxxx" for all directories (so each line xxxx was just a folder name.

I was trying to move all directories in my Downloads folder to the skins folder u see above.

But when I replaced the "cp" with "mv", it all worked fine. How come? I dont see why i can move but not copy?

```
man cp
``` explains about copying directories.

---

