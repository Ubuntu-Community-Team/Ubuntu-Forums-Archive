---
title: "~Name/.profile ---- Not Impacting Terminal"
date: 2010-05-02
forum: General Help
---

### Post by jv2112 on 2010-05-02
I have edited my profile for bash and it does not impact the Terminals I open in the GUI. If I open a TTY it does. How do I update for both ........:confused:

---

### Post by steviefordi on 2010-05-02
~/.profile is only read from a login shell. Try making your edits in ~/.bashrc instead.

---

### Post by jv2112 on 2010-05-02
Perfect !!!!

Anyway of syncing besides the manual method ?  

Thanks !!!!! \\:D/

---

### Post by steviefordi on 2010-05-02
Sorry, I don't follow what you mean by syncing. Can you be more descriptive?

---

### Post by jv2112 on 2010-05-02
When I make a change to one it updates the other. So both are the same.

---

### Post by krismatth3 on 2010-05-02
Only make the change to .bashrc. It should be executed at terminal login too. If it isn't, call it from .profile:  ```
 . ~/.bashrc 
```

---

### Post by ibuclaw on 2010-05-02
Another (possibly more rememberable) way would be
```
source ~/.bashrc
```


Regards

---

### Post by jv2112 on 2010-05-02
Great , Thanks :P

Nice & Simple........

---

