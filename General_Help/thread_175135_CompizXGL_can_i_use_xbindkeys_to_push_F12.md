---
title: "Compiz/XGL can i use xbindkeys to push F12?"
date: 2006-05-12
forum: General Help
---

### Post by jebber007 on 2006-05-12
I'm running Dapper Beta with the newest Compiz/XGL. I'm trying to bind the application switcher button on my MX1000 to F12, but it won't run!! I can run xvkbd -text "\[F12]"

or 

xte "key F12"

from the command line and it works fine, but for some odd reason, it doesn't work when I use xvbindkeys to bind it to a mouse button. (Note pushing F1 to get help DOES work, so I know I have the format of xvbindkeys correct. See below)

Here is my .xbindkeysrc:

```
"xvkbd -text "\[F12]""
  b:10
```

Anyone even attempt this or know why it wouldn't work??

Thanks all!!
Jeb

---

