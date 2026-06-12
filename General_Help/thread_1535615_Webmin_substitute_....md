---
title: "Webmin substitute ...?"
date: 2010-07-21
forum: General Help
---

### Post by agimtirana on 2010-07-21
Hello,

I am switching from CentOS, so I am new in Ubuntu.
Seems  that Ubuntu don't like webmin. Is any webmin substitute, other than eBox?

Thanks!

---

### Post by agimtirana on 2010-07-21
Up

---

### Post by kimda on 2010-07-21
Try this to get webmin working. 

[http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/](http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/)

---

### Post by SwellJoe on 2010-07-31
That tutorial shouldn't be necessary in the latest devel package of Webmin. Webmin doesn't actually need that library at all, it uses the newer variant, by default, but the package had some vestigial auto-generated dependencies making it look like it was needed (the tools to auto-generate dependencies don't understand deps wrapped up in exceptions that aren't mandatory to run).

Anyway, it's been fixed, and Webmin/Usermin/Virtualmin/Cloudmin all run fine on Ubuntu 10.04.

---

