---
title: "chown and skip dot and dot-dot"
date: 2011-03-05
forum: General Help
---

### Post by noloader on 2011-03-05
Hi All,
 
I issued chown '-hR <user>:<group> *' on a directory. chown also change dot and dot-dot in cwd and all subirectories. How do I go about recursively changing ownership without changing dot and dot-dot?
 
Jeff

---

### Post by sanderd17 on 2011-03-05
> **noloader said:**
> Hi All,
 
I issued chown '-hR <user>:<group> *' on a directory. chown also change dot and dot-dot in cwd and all subirectories. How do I go about recursively changing ownership without changing dot and dot-dot?
 
Jeff

do 
```

cd ..
shown -hR <user>:<group> dir_name/*

```

---

### Post by noloader on 2011-03-05
> **sanderd17 said:**
> do 
```

cd ..
shown -hR <user>:<group> dir_name/*

```
 
Thanks sanderd. Is there a switch to skip the dots? Nothing in the man pages jumped out. (It seems to me its *not* uncommon, and there should be an easy way to do it).
 
Jeff

---

