---
title: "Run script on wake (10.04)"
date: 2010-05-17
forum: General Help
---

### Post by radeon21 on 2010-05-17
I want to run a script on wake but it doesn't look like /etc/acpi/resume.d exists in Lucid.  I tried creating it anyway, but I didn't have any luck.  Is this because HAL has been removed?  Is there a new method in Lucid?

---

### Post by radeon21 on 2010-05-17
Shameless bump

---

### Post by jrc03c on 2010-07-15
Another shameless bump.

---

### Post by btindie on 2010-07-15
Do you mean run a script on resume from suspend?
 
Have you got the pm-utils package installed? Take a look at the README for that package to see how it works - /usr/share/doc/pm-utils/README. To see the files it installed type:```
dpkg -L pm-utils | less
```
 
You need to create a script in /etc/pm/sleep.d/ that performs an action when it receives either a *thaw* or *resume* command. Use the ones in /usr/lib/pm-utils/sleep.d/ as an example.

---

