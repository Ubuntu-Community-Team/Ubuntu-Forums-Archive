---
title: "how can i show my installed programs"
date: 2010-05-21
forum: General Help
---

### Post by s.shawky on 2010-05-21
i have installed alot of progams but i cant see most of them in applications menu is there any way enables me to do that

---

### Post by Rubi1200 on 2010-05-21
If you have installed programs that only work from the command line they will not show up in the menus.

However, to check right-click on the Applications panel > Edit menus and see if they are there.

---

### Post by s.shawky on 2010-05-21
thank you you vey much that is i want

---

### Post by alecbenzer on 2010-05-21
```
dpkg --get-selections
``` should give you a list of all packages installed through apt. though it's probably a very long list, if you're looking for something you can use grep to search the output.```
dpkg --get-selections | grep my-app 
```

---

