---
title: "apt-build ignores custom repo"
date: 2012-10-02
forum: General Help
---

### Post by fly-away on 2012-10-02
```
echo "deb-src http://debian.sur5r.net/i3/ precise universe" >> /etc/apt/sources.list
```

"apt-get source i3-wm" give me i3-wm-4.3, but "apt-build source i3-wm" download version from official repos (4.1.2).
How can I fix apt-build?

---

