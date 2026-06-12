---
title: "disable boot Init.d scripts"
date: 2010-09-29
forum: General Help
---

### Post by StOoZ on 2010-09-29
any idea how to disable start-up scripts without uninstalling the program?
I have mysql & ssh running, usually I dont use them, and I know I can stop then with 'stop', but is there a way to permanently disable them, and when I will need to use one, I will turn it on.


thanks,

---

### Post by lukeiamyourfather on 2010-09-29
Remove the links to the script in the folders for each runlevel (e.g. rc.5).

---

