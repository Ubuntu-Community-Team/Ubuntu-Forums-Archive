---
title: "priveleges in Nautilus"
date: 2009-07-06
forum: General Help
---

### Post by raymondvillain on 2009-07-06
How does one open Nautilus ("Places" on the taskbar) with priveleges?  I am the only user (no other accounts) and I want to use Nautilus to shift files around, delete directories, etc.

I can do just about anything from a terminal window, but some tasks would be easier with Nautilus.

Is there a way to start Nautilus so that the system recognizes me as the "super-user" and automatically gives me permission to move files and directories, etc.?

---

### Post by taurus on 2009-07-06
Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by raymondvillain on 2009-07-06
Thanks so much, Taurus.

I will long remember "gksudo nautilus"!

---

### Post by DeMus on 2009-07-06
> **raymondvillain said:**
> Thanks so much, Taurus.

I will long remember "gksudo nautilus"!


I don't want to spoil your fun, but be very careful what you're doing.
With super-user rights you can destroy your installation easily. You won't be the first to do that. No, not me, I never use super rights except for installing new software.

The fact that taurus just gave you the code without any warning is not good. When you don't know what you are doing it is asking for trouble. I do expect to see you here soon asking for help how to get things back because you "accidentally" deleted something, or you changed file or folder properties and now can't access them anymore.

Be very careful. Normally spoken you don't need super-user rights when using Nautilus. That's why Linux is build as it is: safe. You want to change that.

---

