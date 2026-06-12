---
title: "gnome-terminal -e &lt;multiple commands&gt;"
date: 2011-08-23
forum: General Help
---

### Post by aeronutt on 2011-08-23
With xterm, I can do the following, and the scripts are executed sequentially in a single xterm:

*xterm -e 'script1.sh;script2.sh'*

But with gnome-terminal, when I do:

*gnome-terminal -e script1.sh;script2.sh*

It runs them in parallel in 2 different terminals.

I've tried a few combinations of ", and ', around the scrips, but no difference.

Any ideas?

---

### Post by dave01945 on 2011-08-23
this might be what your looking for

[http://ubuntuforums.org/showthread.php?t=882185](http://ubuntuforums.org/showthread.php?t=882185)

---

### Post by aeronutt on 2011-08-23
> **dave01945 said:**
> this might be what your looking for

[http://ubuntuforums.org/showthread.php?t=882185](http://ubuntuforums.org/showthread.php?t=882185)

Bingo!! Thank you!

---

