---
title: "'locate' finds nonexistant folders"
date: 2010-06-20
forum: General Help
---

### Post by moment92 on 2010-06-20
Hello!
I just removed another admin user and deleted all its folders. Nevertheless, "locate" tells me, that the directory /home/username and some other such directories still exist. Why does it think they still exist and how to fix it? I know, that it's not a big problem, but it's annoying.

---

### Post by wojox on 2010-06-20
Try rebooting and run locate again.

---

### Post by Zip247 on 2010-06-20
from the locate man page:

By default, locate does not check whether files found in database still
       exist.  locate can never report files created  after  the  most       recent update of the relevant database

you could run

> sudo updatedb

and then try locate again.

---

### Post by moment92 on 2010-06-20
Thanks, updatedb worked.

---

### Post by wojox on 2010-06-20
Please mark the post as Solved.

---

