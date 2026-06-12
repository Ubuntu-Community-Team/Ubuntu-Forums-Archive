---
title: "Source package not in repository"
date: 2009-08-01
forum: General Help
---

### Post by nr0mx on 2009-08-01
How do I enable source packages in my repository ? Should it be there by default ? I am running Janty.

```

$ sudo apt-get source nautilus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for nautilus

```

---

### Post by michy99 on 2009-08-01
System->Administration->Software Sources. Make sure there is a check mark by Source Code.

---

### Post by nr0mx on 2009-08-01
> **michy99 said:**
> System->Administration->Software Sources. Make sure there is a check mark by Source Code.
Thanks, it wasn't checked. It had a "-" instead of an empty checkbox which my brain skipped over!

---

