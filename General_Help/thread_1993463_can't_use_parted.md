---
title: "can't use parted"
date: 2012-06-02
forum: General Help
---

### Post by luofeiyu on 2012-06-02
when  i  input :
parted
parted: error while loading shared libraries: libparted.so.2: cannot open shared object file: No such file or directory
how can i solve it?

---

### Post by oldos2er on 2012-06-02
How did you install it? Try ```
sudo apt-get install --reinstall parted
```

---

