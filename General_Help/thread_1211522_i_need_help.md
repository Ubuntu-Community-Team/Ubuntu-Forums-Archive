---
title: "i need help"
date: 2009-07-12
forum: General Help
---

### Post by spartan119 on 2009-07-12
whenever i start my update mananger and try to install up dates it comes up with this error message:E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i tryed to put dpkg --configure -a in the terminal and  it said i need a super user privilage. im a total newbie at this my ubuntu version is 8.04. i hope this helps

---

### Post by McNils on 2009-07-12
you must have root privileges.

```
sudo dpkg --configure -a
```

should do it. you get no feedback when typing the password.

---

### Post by spartan119 on 2009-07-12
it still says that i need a super user privilege but it lets me update now so thanks

---

