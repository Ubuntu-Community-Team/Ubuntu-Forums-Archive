---
title: "Firefox keeps spawning new child threads"
date: 2010-08-08
forum: General Help
---

### Post by Anulith on 2010-08-08
Hello,

After a recent upgrade, every time I try to launch firefox all that happens is that it continuously spawns new child threads.  No window ever opens and the processor is spun up 100%.  I have tried to completely remove firefox, yet when I type firefox at the command line the same thing happens.  I do a whereis firefox and it reports nothing.

Any suggestions on how to clean this up and get Firefox back in working order?

Thanks

edit:

Ok, so I finally found my problem.  I had a script for starting firefox in my ~/bin folder that I had forgot about.  This script lazily executed "firefox" on the last line instead of a full path.  So, what happened was that the script just kept executing itself over and over.  I guess upon update, my home bin folder became higher in the path than /usr/bin.

---

