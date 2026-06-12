---
title: "Error: Dependency is not satisfiable: libhpricot-ruby1.8"
date: 2011-05-20
forum: General Help
---

### Post by ChaosChris2009 on 2011-05-20
I tried installing a .deb package from [http://apticon.wordpress.com/]("http://apticon.wordpress.com/")

but it gives this

```
Error: Dependency is not satisfiable: libhpricot-ruby1.8
```

What do I do?

:confused:

---

### Post by hulkman on 2011-05-20
libhpricot-ruby1.8 appears in the repositories of both Ubuntu 10.10 and 11.04.  I think mabey you need to enable the software sources.  To do this:

1. Open the "Ubuntu Software Center"
2. Left click the "Edit" menu and select "Software Sources..."
3. Make sure all the boxes except the Cdrom box is checked.  (Note: if you check the Cdrom box, it will be constantly asking you to insert your Ubuntu CD, so I always leave it unchecked.)
4. Click close.
5. Wait until the two green rotating arrows in the "Ubuntu Software Center" disappear.
6. Try installing "Eve Installer" again.

---------------------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place for packages!

---

### Post by mc4man on 2011-05-20
Maybe ck. your software sources and make sure that the 1st 4 are enabled
(the package [you need is in Universe]("http://packages.ubuntu.com/natty/libhpricot-ruby1.8")
If they aren't then enable, click close and reload.
In any case then run in a terminal
```
sudo apt-get update
```

---

