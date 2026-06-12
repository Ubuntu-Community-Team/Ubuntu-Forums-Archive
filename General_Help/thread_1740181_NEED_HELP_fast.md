---
title: "NEED HELP fast"
date: 2011-04-26
forum: General Help
---

### Post by kolmad on 2011-04-26
i need some one to convert this .bat file:
@echo off 
cd bin
java -Xmx800M Server
pause

---

### Post by kolmad on 2011-04-26
bump

---

### Post by cipherboy_loc on 2011-04-26
Try something like this:

```

#!/bin/bash

cd /path/to/some/random/bin/directory
java -Xmx800M Server
echo "Press any key to continue... " ; read

```

Cipherboy

---

### Post by kolmad on 2011-04-28
it didnt work :/

---

### Post by DaithiF on 2011-04-28
seems very similar to your post from a few weeks ago:
[http://ubuntuforums.org/showthread.php?p=10607882#post10607882](http://ubuntuforums.org/showthread.php?p=10607882#post10607882)

can you not apply what you learned from that ?

---

