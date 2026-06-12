---
title: "updated to 10.04 and phpmyadmin no worky"
date: 2010-05-08
forum: General Help
---

### Post by bigtimslim on 2010-05-08
I have a typical lamp setup. I updated to 10.04 and I can't seem to access phpmyadmin now. Apache and mysql seem to be working fine. I have tried restarting them both and have reinstalled phpmyadmin.

Any suggestions?

edit: When I say not working, I mean I try to navigate to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) and get page not found.

---

### Post by dracayr on 2010-05-08
Well does the folder phpmyadmin exist?

dracayr

---

### Post by bigtimslim on 2010-05-08
here is what I've got. Should it exist in my web root?

root@tim-laptop:/home/tim# find / -name phpmyadmin
/etc/phpmyadmin
/usr/share/doc/phpmyadmin
/usr/share/doc-base/phpmyadmin
/usr/share/phpmyadmin
/usr/share/dbconfig-common/data/phpmyadmin
/var/lib/doc-base/documents/phpmyadmin
/var/lib/doc-base/omf/phpmyadmin
/var/lib/mysql/phpmyadmin
/var/lib/phpmyadmin

---

### Post by bigtimslim on 2010-05-08
Hell. I should probably just backup my stuff and start the lamp setup from scratch.

---

### Post by Sureshot324 on 2010-05-08
I have the exact same problem.  phpmyadmin worked fine in Ubuntu 9.10, but when I updated to 10.4 it stopped working.  I do not have a phpmyadmin folder in /var/www.

---

### Post by vinayakgit on 2010-07-19
sudo ln -s /usr/share/phpmyadmin /var/www


Yap..This has to work:guitar::lolflag:):P

---

