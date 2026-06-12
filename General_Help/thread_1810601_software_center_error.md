---
title: "software center error"
date: 2011-07-23
forum: General Help
---

### Post by woodmaster on 2011-07-23
Get this error.  Ubuntu 11.04 Classic.  Won't let me install anything, even with apt from terminal.  Any ideas?

---

### Post by oldos2er on 2011-07-23
```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update
```

---

### Post by woodmaster on 2011-07-23
**[COLOR="Lime"]You sir, are awesome![/COLOR]**

---

### Post by oldos2er on 2011-07-23
I could do without the "sir," but you're welcome.

---

