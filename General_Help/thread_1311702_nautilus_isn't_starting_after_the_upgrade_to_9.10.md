---
title: "nautilus isn't starting after the upgrade to 9.10"
date: 2009-11-02
forum: General Help
---

### Post by cherva on 2009-11-02
When I try to start nautilus from the terminal I get:
```
(nautilus:10267): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
nautilus: symbol lookup error: nautilus: undefined symbol: g_reload_user_special_dirs_cache
```

---

### Post by burgechris on 2009-11-02
Agree...having the same problem.  Popping the popcorn and seeing if anyone else is hosed.  :popcorn:  :o

---

### Post by cherva on 2009-11-04
I solved my problem by removing anything from my /usr/local dir :)
```
sudo rm /usr/local/* -r
``` **BEFORE THIS CHECK IF THERE IS ANYTHING YOU USE IN THIS DIRECTORY**

---

