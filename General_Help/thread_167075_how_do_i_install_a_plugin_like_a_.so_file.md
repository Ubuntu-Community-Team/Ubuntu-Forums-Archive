---
title: "how do i install a plugin like a .so file?"
date: 2006-04-27
forum: General Help
---

### Post by dagamer on 2006-04-27
how do i install a plugin like a .so file?](*,)

---

### Post by Qrk on 2006-04-27
Make a symbolic link to it in your plugins directory (I assume for mozilla firefox). 

```
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /path/to/plugin.so
```

---

