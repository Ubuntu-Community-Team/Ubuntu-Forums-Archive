---
title: "Menu item error?"
date: 2010-08-27
forum: General Help
---

### Post by Puzzled Guy on 2010-08-27
Whenever I install a game, then click it in the menu, it says it cannot find the file. I have to manually change the menu item's location from gamename to /usr/games/gamename.

Does anyone know how to fix this?
The $PATH variable only says /usr/local/bin:/usr/bin:/bin. The /usr/games directory isn't there anymore. It worked fine until recently.

I think the problem is in the $PATH variable. I tried 'PATH=$PATH:/usr/games' but that doesn't work, or, it does but only until I close the terminal, then it's gone again.

How do I put /usr/games back into the  $PATH variable? Besides the given method that failed, of course.

Having to manually change the properties every time is quite annoying.

---

### Post by geirha on 2010-08-27
```
$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

```

That file is read when you log in. The file was installed when I installed Ubuntu.

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

---

### Post by Puzzled Guy on 2010-08-27
Solved!
Thanks, worked perfectly. Just had to logout and login again for changes to take effect.

Thanks a lot!

---

