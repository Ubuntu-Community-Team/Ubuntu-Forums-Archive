---
title: "Shouldn't 'ps' command show my apache2 daemon?"
date: 2010-01-01
forum: General Help
---

### Post by oospill on 2010-01-01
I've got Apache2 installed on my Ubuntu Desktop [laptop] .. and it runs at startup.  [Going to 127.0.0.1 proves this!] .. when I open up a terminal, shouldn't running 'ps' show the Apache2 daemon?

thanks!

---

### Post by oospill on 2010-01-01
whoa .. when I typed 'ps aux', it shows a LOT of processes..  so why isn't apache2 showing up when I type just plain 'ps'?  does is only show process for *that* terminal ?? (ctrl+alt+f1 etc)??

thanks!

---

### Post by falconindy on 2010-01-01
ps without arguments won't show processes that the user executing it doesn't own. 'ps aux' shows processes from **a**ll **u**sers.

For more info: man ps

---

### Post by oospill on 2010-01-01
excellent.. thankyou..  I just figured that out..  apache2 is running under root.  learned this by running top!!

ubuntu rocks!

---

