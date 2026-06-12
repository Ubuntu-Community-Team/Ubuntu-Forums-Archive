---
title: "Copy &quot;group&quot; permissions to &quot;other&quot; permissions"
date: 2009-11-14
forum: General Help
---

### Post by antiloop222 on 2009-11-14
Hello, I have several files with different permissions set on the group (some files with g+x other with g+w...). Nothing is set for other.

My aim is to copy the group permissions to the other permissions (I would like to avoid the brutal solution chmod -R o+xw *)

Any ideas ?

Thanks

---

### Post by diesch on 2009-11-14
```
chmod o=g
```

---

### Post by antiloop222 on 2009-11-14
Thank you very much, i missed that in the man page :-/

---

