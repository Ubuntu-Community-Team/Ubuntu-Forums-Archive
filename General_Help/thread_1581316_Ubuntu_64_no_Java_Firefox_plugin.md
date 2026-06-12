---
title: "Ubuntu 64 no Java Firefox plugin"
date: 2010-09-24
forum: General Help
---

### Post by n1unqn on 2010-09-24
Ubuntu Desktop 10.04 64 no Java Firefox plugin

sudo apt-get install sun-java6-plugin

gets

Couldn't find package sun-java6-plugin

:mad:

---

### Post by Hobgoblin on 2010-09-24
[Did you try this?](http://ubuntuforums.org/showthread.php?t=1517979)

---

### Post by n1unqn on 2010-09-24
Thank you it works...

   1. Enable repository: Click System -> Administration -> Software Sources, go to tab Other Software and tick the first entry ("partner"). Close and confirm the "Reload".
   2. Install Sun Java: Go to Applications -> Software-Center -> Search for "sun java" and install the first package ("Sun Java 6.0 Plugin"). You are done!

Someone needs to update the help file in ubuntu with this info. :popcorn:

---

