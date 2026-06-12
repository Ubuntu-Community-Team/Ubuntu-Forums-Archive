---
title: "less command from launcher?"
date: 2011-11-15
forum: General Help
---

### Post by LuniTux on 2011-11-15
Hello,

I am trying to run the less command from a launcher.

I know I can run a command like top using "xterm -e top" but I want to be able to run the command "xterm less -f <mylog>"

any ideas?

---

### Post by lechien73 on 2011-11-15
You can create a launcher with the command:

```
xterm -e less -f /path-to-log/logfilename
```

---

### Post by VCoolio on 2011-11-15
or use a zenity window; install zenity, then ```

less -f /path/yourlog | zenity --text-info
```

---

### Post by LuniTux on 2011-11-15
YAY!!!!

Thank you

---

### Post by Slim Odds on 2011-11-15
or you could install xless

---

