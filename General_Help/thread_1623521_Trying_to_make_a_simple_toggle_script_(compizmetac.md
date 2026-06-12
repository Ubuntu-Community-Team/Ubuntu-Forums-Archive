---
title: "Trying to make a simple toggle script (compiz/metacity)"
date: 2010-11-16
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-11-16
i wanted to be able to hot key it
```

#!/bin/bash
if [ 0`pidof metacity` -gt 0 ]; then
    compiz --replace
else
    metacity --replace
fi
exit

```can some one fill in the blanks in my code

---

### Post by yuki-nagato on 2010-11-16
metacity --replace       is the code for replacing compiz with metacity as the window manager

compiz --replace       is the code for replacing metacity with compiz as the window manager

Since I'm too lazy to make a proper script, I just created two shortcuts.  One to each command and click whichever one is needed.

---

### Post by pqwoerituytrueiwoq on 2010-11-16
thanks updates post

---

### Post by pqwoerituytrueiwoq on 2010-11-16
i found a command thats readout will tell you if it is running
```
pidof metacity
```if metacity is running i get a number if not it returns null just not sure how to use it in the script
edit got that part

---

