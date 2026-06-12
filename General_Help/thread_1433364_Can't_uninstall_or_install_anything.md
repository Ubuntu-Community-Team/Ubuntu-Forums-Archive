---
title: "Can't uninstall or install anything"
date: 2010-03-18
forum: General Help
---

### Post by NintendoTogepi on 2010-03-18
So a couple days back I tried installing Mythbuntu onto my current Ubuntu, but it froze and I didn't care that much so I canceled it and shut it down.

Now whenever I try to remove the package or install a new package (of any kind) I get:

```
An error occurred

The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


```

Help?

---

### Post by Ozymandias_117 on 2010-03-18
Just do what it says =P run ```
sudo dpkg --configure -a
```

---

### Post by NintendoTogepi on 2010-03-19
That takes me to some weird set up for Mythbuntu where I eventually get stuck and I can't do anything, and then it runs a bunch of errors.

---

### Post by Ozymandias_117 on 2010-03-19
What errors is it giving you?

---

