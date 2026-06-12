---
title: "Copy with Nautilus and retain properties"
date: 2011-05-01
forum: General Help
---

### Post by wily_one on 2011-05-01
I need to copy some files/folders around but retain the current ownership & permission settings and timestamp on each file.  Can this be done in the GUI (Nautilus)?

Thanks

---

### Post by wily_one on 2011-05-03
Not possible?  Or no one knows?

---

### Post by fdrake on 2011-05-03
```
sudo nautilus /
```
you can copy and move anyfile anywhere, without changing the permissions..

---

### Post by TeoBigusGeekus on 2011-05-03
Don't know about nautilus, but you can do it from terminal with cp and the -p option.

---

### Post by wily_one on 2011-05-15
> **fdrake said:**
> ```
sudo nautilus /
```you can copy and move anyfile anywhere, without changing the permissions..
By default it certainly does not work as you describe.  Timestamps and permissions are retained, but not the owner/group.

---

### Post by wily_one on 2011-05-15
**[SOLVED]**

Found the solution.  I was invoking nautilus with sudo, and it was doing as shown; changing owner:group to root:root.

Looking around on Google I saw references to gksudo.  I tried invoking nautilus with that, and presto chango it keeps the file ownership as is.  Yay me.

---

