---
title: "Can no longer open folders, missing handling application. Please Help!"
date: 2009-08-11
forum: General Help
---

### Post by Lavaeagle on 2009-08-11
I somehow managed to uninstall the program that handles opening folders for example when i go to Places>Documents the ending result is:

No application is registered as handling this file

I uninstalled evolution, and I may have uninstalled something else unintentionally.

Might someone know what this is?

---

### Post by Lavaeagle on 2009-08-11
System>Administration>Synaptic Package Manager
Install Nautilus

Ta da!

---

### Post by michy99 on 2009-08-11
Uninstalling Evolution is not a good idea, even if you don't use it. You may have uninstalled Nautilus (the file browser) unintentionally. Enter this in a terminal:```
sudo apt-get install nautilus
```

EDIT: I guess I type too slow!

---

### Post by Lavaeagle on 2009-08-11
Thank you for replying never the les this may help some other people out ;)

---

