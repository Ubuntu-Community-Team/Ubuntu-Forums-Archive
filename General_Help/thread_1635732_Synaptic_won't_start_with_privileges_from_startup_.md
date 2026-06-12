---
title: "Synaptic won't start with privileges from startup menu"
date: 2010-12-02
forum: General Help
---

### Post by knutschr on 2010-12-02
I have put som programs in System -> Preferences -> Startup.
That works fine, except that Synaptic starts without asking for a password, and therefor also without superuser privileges.
Is there a way I can change the command so that it will ask for a password?

---

### Post by arubislander on 2010-12-02
There is. If you add
```
gksudo
``` in front of the synaptic command, with a space between them, you will be prompted for your password before synaptic loads.

---

