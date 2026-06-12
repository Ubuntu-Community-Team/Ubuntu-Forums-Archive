---
title: "deleted phpmyadmin dir, how to remove with apt-get?"
date: 2006-03-02
forum: General Help
---

### Post by mad_phoenix on 2006-03-02
Hi,
  I stupidly forgot that I installed phpmyadmin with apt-get (instead of just downloading and unpacking the tarball).  So I just deleted the directory from phpmyadmin.  Now, apt-get still thinks its there, but also can't remove it.  When I try to do apt-get remove phpmyadmin, this is what I get:

```
Removing phpmyadmin ...
/var/lib/dpkg/info/phpmyadmin.prerm: line 12: db_get: command not found
dpkg: error processing phpmyadmin (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm really in a bind here.  How can I get apt-get to remove whatever remains of phpmyadmin?

---

### Post by Ramses de Norre on 2006-03-02
Maybe when you first install it through apt-get and the remove it.

---

### Post by mad_phoenix on 2006-03-02
No, it says that phpmyadmin is already installed when I try to install it again.

---

### Post by Koybe on 2006-03-02
Did you try?
```
apt-get --reinstall install phpmyadmin
```

---

### Post by mad_phoenix on 2006-03-02
That worked great, thanks a lot!

---

