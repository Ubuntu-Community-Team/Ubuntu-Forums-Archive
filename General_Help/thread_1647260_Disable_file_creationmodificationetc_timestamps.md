---
title: "Disable file creation/modification/etc timestamps?"
date: 2010-12-17
forum: General Help
---

### Post by viktorzk on 2010-12-17
Hello,

Can I disable the file creation/modification/access/etc timestamps? Or set them all to the same value and stop the system from updating them? I would rather keep track of all information that I need manually.

Thanks!

---

### Post by HermanAB on 2010-12-17
$ man touch
$ man mount

---

### Post by dcstar on 2010-12-17
> **viktorzk said:**
> Hello,

Can I disable the file creation/modification/access/etc timestamps? Or set them all to the same value and stop the system from updating them? I would rather keep track of all information that I need manually.

Thanks!

/etc/fstab option **noatime**

---

### Post by viktorzk on 2011-03-01
deleted

---

### Post by viktorzk on 2011-03-02
deleted

---

### Post by viktorzk on 2011-03-06
deleted

---

